<h1 align="center">nnn plugins</h1>

<p align="center"><img src="https://i.imgur.com/14iPDIq.png" /></p>
<p align="center"><i>image preview with plugin thumb</i></p>

Plugins extend the capabilities of `nnn`. They are scripts which `nnn` can communicate with and trigger. This mechanism fits perfectly with the fundamental design to keep the core file manager lean and fast, by delegating repetitive (but not necessarily file manager-specific) tasks to the plugins.

The currently available plugins are listed below.

| Plugin (a-z) | Lang | Deps | Description |
| --- | --- | --- | --- |
| boom | sh | [moc](http://moc.daper.net/) | Play random music from dir |
| dups | sh | find, md5sum,<br>sort uniq xargs | List non-empty duplicate files in current dir |
| checksum | sh | md5sum,<br>sha256sum | Create and verify checksums |
| drag-file | sh | [dragon](https://github.com/mwh/dragon) | Drag and drop files from nnn |
| drop-file | sh | [dragon](https://github.com/mwh/dragon) | Drag and drop files into nnn |
| fzcd | sh | fzy/fzf<br>(optional fd) | Change to the directory of a file/directory selected by fzy/fzf |
| fzy-open | sh | fzy, xdg-open | Fuzzy find a file in dir subtree and edit or xdg-open |
| getplugs | sh | curl | Update plugins |
| gutenread | sh | curl, unzip, w3m<br>[epr](https://github.com/wustho/epr) (optional)| Browse, download, read from Project Gutenberg |
| hexview | sh | xxd | View a file in hex in `$PAGER` |
| imgresize | sh | [imgp](https://github.com/jarun/imgp) | Resize images in dir to screen resolution |
| imgur | bash | - | Upload an image to imgur (from [imgur-screenshot](https://github.com/jomo/imgur-screenshot)) |
| ipinfo | sh | curl, whois | Fetch external IP address and whois information |
| kdeconnect | sh | kdeconnect-cli | Send selected files to an Android device |
| mediainf | sh | mediainfo | Show media information |
| moclyrics | sh | [ddgr](https://github.com/jarun/ddgr), [moc](http://moc.daper.net/) | Show lyrics of the track playing in moc |
| mocplay | sh | [moc](http://moc.daper.net/) | Append (and/or play) selection/dir/file in moc|
| ndiff | sh | vimdiff | Diff for selection (limited to 2 for directories) |
| nmount | sh | pmount, udisks2 | Toggle mount status of a device as normal user |
| notes | sh | - | Open a quick notes file/dir in `$EDITOR` |
| nwal | sh | nitrogen | Set image as wallpaper using nitrogen |
| oldbigfile | sh | find, sort | List large files by access time |
| organize | sh | file | Auto-organize files in directories by file type |
| pastebin | sh | - | Paste contents of a text a file ix.io |
| pdfview | sh | pdftotext/<br>mupdf-tools | View PDF file in `$PAGER` |
| picker | sh | nnn | Pick files and list one per line (to pipe) |
| pywal | sh | pywal | Set image as wallpaper, change terminal colorscheme |
| readit | sh | pdftotext, mpv,<br>pico2wave | Read a PDF or text file aloud |
| ringtone | sh | date, ffmpeg | Create a variable bitrate mp3 ringtone from file |
| splitjoin | sh | split, cat | Split file or join selection |
| suedit | sh | sudoedit/sudo/doas | Edit file using superuser permissions |
| sxiv | sh | sxiv | View images in dir, set wallpaper, copy path ([config](https://wiki.archlinux.org/index.php/Sxiv#Assigning_keyboard_shortcuts))|
| thumb | sh | [lsix](https://github.com/hackerb9/lsix) | View thumbnail of an image or dir of images |
| transfer | sh | curl | Upload file to transfer.sh |
| uidgid | sh | ls, less | List user and group of all files in dir |
| upgrade | sh | curl | Upgrade nnn manually on Debian 9 Stretch |
| vidthumb | sh | [ffmpegthumbnailer](https://github.com/dirkvdb/ffmpegthumbnailer),<br>[lsix](https://github.com/hackerb9/lsix) | Show video thumbnails in terminal |
| viuimg | sh | [viu](https://github.com/atanunq/viu), less | View an image or images in dir in `$PAGER` |

## Installing plugins

The following command installs all plugins:

    curl -Ls https://raw.githubusercontent.com/jarun/nnn/master/plugins/getplugs | sh

Plugins are installed to `${XDG_CONFIG_HOME:-$HOME/.config}/nnn/plugins`. You can run the `getplugs` plugin later to update the plugins. It backs up earlier plugins.

**NOTE:** `getplugs` also downloads the launcher `nlaunch` and tries to place it at `/usr/local/bin/` using `sudo`. If it fails you have to place `nlauch` manually somewhere in your `$PATH`.

## Executing plugins

**Method 1:** Directly with <kbd>:key</kbd>:

    export NNN_PLUG='o:fzy-open;p:mocplay;d:ndiff;m:nmount;n:notes;v:viuimg;t:thumb'

With this, plugin `fzy-open` can be run with the keybind <kbd>:o</kbd>, `mocplay` can be run with <kbd>:p</kbd> and so on... The key vs. plugin pairs are shown in the help and config screen. Up to 10 plugins can have such keybinds.

**Method 2:** Use the _pick plugin_ shortcut to visit the plugin directory and execute a plugin. Repeating the same shortcut cancels the operation and puts you back in the original directory.

## Create your own plugins

Plugins are a powerful yet easy way to extend the capabilities of `nnn`.

Plugins are scripts that can be written in any scripting language. However, POSIX-compliant shell scripts runnable in `sh` are preferred.

Each script has a _Description_ section which provides more details on what the script does, if applicable.

The plugins reside in `${XDG_CONFIG_HOME:-$HOME/.config}/nnn/plugins`.

When `nnn` executes a plugin, it does the following:
- Change to the directory where the plugin is to be run (`$PWD` pointing to the active directory)
- Passes two arguments to the script:
    1. The hovered file's name
    2. The working directory (might differ from `$PWD` in case of symlinked paths; non-canonical)
- Sets the environment variable `NNN_PIPE` used to control `nnn` active directory.

Plugins can also access the current selections by reading the `.selections` file in the config directory (See the `ndiff` plugin for example).

#### Controlling `nnn`'s active directory
`nnn` provides a mechanism for plugins to control its active directory.
The way to do so is by writing to the pipe pointed by the environment variable `NNN_PIPE`.
The plugin should write a single string in the format `<number><path>` without a newline at the end. For example, `1/etc`.
The number indicates the context to change the active directory of (0 is used to indicate the current context).

For convenience, we provided a helper script named `.nnn-plugin-helper` and a function named `nnn_cd` to ease this process. `nnn_cd` receives the path to change to as the first argument, and the context as an optional second argument.
If a context is not provided, it is asked for explicitly.
Usage examples can be found in the Examples section below.

#### Examples
There are many plugins provided by `nnn` which can be used as examples. Here are a few simple selected examples.

- Show the git log of changes to the particular file along with the code for a quick and easy review.
   ```sh
    #!/usr/bin/env sh
    git log -p -- "$1"
    ```
    
- Change to directory in clipboard using helper script
    ```sh
    #!/usr/bin/env sh
    . $(dirname $0/.nnn-plugin-helper)

    nnn_cd "$(xsel -ob)"
    ```

- Change direcory to the location of a link using helper script with specific context (current)
    ```sh
    #!/usr/bin/env sh
    . $(dirname $0/.nnn-plugin-helper)

    nnn_cd "$(dirname $(readlink -fn $1))" 0
    ```
    
- Change to arbitrary directory without helper script
    ```sh
    #!/usr/bin/env sh
    echo -n "cd to: "
    read dir
    
    echo -n "0$dir" > $NNN_PIPE
    ```

## Contributing plugins

Please keep non-portable commands (like `notify-send`) commented so users from any other OS/DE aren't surprised.

The plugins should be executable. Please add an entry in the table above.

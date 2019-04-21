<h2 align="center">nnn (<i>type less, do more, way faster</i>)</h2>

<p align="center">
<a href="https://github.com/jarun/nnn/releases/latest"><img src="https://img.shields.io/github/release/jarun/nnn.svg?maxAge=600" alt="Latest release" /></a>
<a href="http://formulae.brew.sh/formula/nnn"><img src="https://img.shields.io/homebrew/v/nnn.svg?maxAge=600" alt="Homebrew" /></a>
<a href="https://www.archlinux.org/packages/community/x86_64/nnn/"><img src="https://img.shields.io/badge/archlinux-rolling-blue.svg?maxAge=600" alt="Arch Linux" /></a>
<a href="https://packages.debian.org/search?keywords=nnn&searchon=names&exact=1"><img src="https://img.shields.io/badge/debian-10+-blue.svg?maxAge=2592000" alt="Debian Buster+" /></a>
<a href="https://apps.fedoraproject.org/packages/nnn"><img src="https://img.shields.io/badge/fedora-27+-blue.svg?maxAge=2592000" alt="Fedora 27+" /></a>
<a href="https://software.opensuse.org/package/nnn"><img src="https://img.shields.io/badge/opensuse%20leap-15.0+-blue.svg?maxAge=2592000" alt="openSUSE Leap 15.0+" /></a>
<a href="https://packages.ubuntu.com/search?keywords=nnn&searchon=names&exact=1"><img src="https://img.shields.io/badge/ubuntu-17.10+-blue.svg?maxAge=2592000" alt="Ubuntu Artful+" /></a>
</p>

<p align="center">
<a href="https://repology.org/metapackage/nnn"><img src="https://repology.org/badge/tiny-repos/nnn.svg" alt="Availability"></a>
<a href="https://travis-ci.org/jarun/nnn"><img src="https://img.shields.io/travis/jarun/nnn/master.svg?label=travis" alt="Travis Status" /></a>
<a href="https://circleci.com/gh/jarun/workflows/nnn"><img src="https://img.shields.io/circleci/project/github/jarun/nnn.svg?label=circleci" alt="CircleCI Status" /></a>
<a href="https://github.com/jarun/nnn/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-BSD%202--Clause-yellow.svg?maxAge=2592000" alt="License" /></a>
</p>

<p align="center">
<a href="https://www.youtube.com/watch?v=U2n5aGqou9E"><img src="https://i.imgur.com/onpq3vP.png" alt="Click to watch video"/></a>
</p>

<p align="center"><i>3 modes of nnn (light with filter, detail, du analyzer) with memory usage. Click for a demo video.</i></a></p>

`nnn` is one of the fastest and most lightweight file managers (`~55KB` binary, `~3.5MB` resident memory usage, [highly optimized](https://github.com/jarun/nnn/wiki/performance-factors) code). And yet, it doesn't lack in features!

`nnn` works seamlessly with your DE and favourite GUI utilities. It runs on Linux, macOS, Raspberry Pi, BSD, Cygwin, Linux subsystem for Windows and Termux on Android.

Have as many scripts as you want to extend the power of `nnn`! Pick from the available [plugins](https://github.com/jarun/nnn/tree/master/plugins) or add your own.

[Quickstart](#quickstart) and see how `nnn` simplifies long desktop sessions. When you are ready for more, start [hacking `nnn`](https://github.com/jarun/nnn/wiki/hacking-nnn).

*Love smart and efficient utilities? Explore [my repositories](https://github.com/jarun?tab=repositories). Buy me a cup of coffee if they help you.*

<p align="center">
<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RMLTQ76JSXJ4Q"><img src="https://img.shields.io/badge/PayPal-donate-1eb0fc.svg" alt="Donate via PayPal!" /></a>
</p>

#### TABLE OF CONTENTS

- [Features](#features)
- [Installation](#installation)
  - [Library dependencies](#library-dependencies)
  - [Utility dependencies](#utility-dependencies)
  - [From a package manager](#from-a-package-manager)
  - [Release packages](#release-packages)
  - [From source](#from-source)
  - [Shell completion](#shell-completion)
- [Quickstart](#quickstart)
- [Usage](#usage)
  - [Cmdline options](#cmdline-options)
  - [Keyboard shortcuts](#keyboard-shortcuts)
  - [Leader key](#leader-key)
  - [Contexts](#contexts)
    - [Context-specific color](#context-specific-color)
  - [Selection](#selection)
  - [Filters](#filters)
  - [Navigate-as-you-type](#navigate-as-you-type)
  - [File indicators](#file-indicators)
  - [Configuration](#configuration)
  - [SSHFS mounts](#sshfs-mounts)
  - [Help](#help)
- [Plugins](#plugins)
- [Troubleshooting](#troubleshooting)
  - [Tmux configuration](#tmux-configuration)
  - [BSD terminal issue](#bsd-terminal-issue)
  - [Restrict file open](#restrict-file-open)
  - [Restrict 0-byte files](#restrict-0-byte-files)
- [Why fork?](#why-fork)
- [Mentions](#mentions)
- [Developers](#developers)

#### FEATURES

- Modes
  - Detail (default), light
  - Disk usage analyzer (block/apparent)
  - File picker, (neo)vim plugin
- Navigation
  - *Navigate-as-you-type* with auto-select dir, *wild load*
  - 4 contexts (_aka_ tabs _aka_ workspaces)
  - Bookmarks; pin and visit a directory
  - Familiar, easy shortcuts (arrows, <kbd>~</kbd>, <kbd>-</kbd>, <kbd>@</kbd>)
- Sorting
  - Ordered pure numeric names by default (visit _/proc_)
  - Sort by file name, modification time, size
  - Version (_aka_ natural) sort
- Search
  - Instant filtering with *search-as-you-type*
  - Regex and substring match
  - Subtree search (needs fzy)
- Mimes
  - Open with desktop opener or specify a custom app
  - Create, list, extract archive (needs (p)atool)
  - Open all text files in EDITOR (optional)
- Information
  - Detailed file information (stat and file)
  - Media information (needs mediainfo/exiftool)
- Convenience
  - Create, rename files and directories
  - Select files across dirs; all/range selection
  - Copy, move, delete, archive, link selection
  - FreeDesktop compliant trash (needs trash-cli)
  - Show copy, move progress on Linux (needs avdcpmv)
  - Plugin repository
  - SSHFS mounts (needs sshfs)
  - Batch rename (needs vidir)
  - Per-context directory color (default: blue)
  - Spawn a shell in the current directory
  - Launch applications, run a command
  - Run current file as executable
  - Change directory at exit (*easy* shell integration)
  - Edit file in EDITOR or open in PAGER
  - Take quick notes
  - Lock the terminal (needs a locker)
  - Shortcut reference a keypress away
- Unicode support
- Follows Linux kernel coding style
- Highly optimized, static analysis integrated code
- Minimal library dependencies
- Available on many distros

#### INSTALLATION

#### Library dependencies

`nnn` needs a curses library with wide character support (like ncursesw), libreadline and standard libc. It's possible to drop libreadline using the Makefile target `norl`.

#### Utility dependencies

| Dependency | Operation |
| --- | --- |
| xdg-open (Linux), open(1) (macOS), cygstart (Cygwin) | desktop opener |
| file, coreutils (cp, mv, rm), findutils (xargs) | detect type, copy, move and remove files |
| trash-cli | trash files (default: delete) |
| mediainfo / exiftool | multimedia file details |
| atool / patool ([integration](https://github.com/jarun/nnn/wiki/hacking-nnn#integrate-patool)) | create, list and extract archives |
| fzy | app launcher with drop-down menu |
| vidir (from moreutils) | batch rename dir entries |
| sshfs, fusermount(3) | mount, unmount remote over SSHFS |
| vlock (Linux), bashlock (macOS), lock(1) (BSD) | terminal locker |
| advcpmv (Linux) ([integration](https://github.com/jarun/nnn/wiki/hacking-nnn#show-cp-mv-progress)) | copy, move progress |
| `$VISUAL` (else `$EDITOR`), `$PAGER` (less, most), `$SHELL` | fallback vi, less, sh |

#### From a package manager

- [Alpine Linux](https://pkgs.alpinelinux.org/packages?name=nnn) (`apk add nnn`)
- [Arch Linux](https://www.archlinux.org/packages/community/x86_64/nnn/) (`pacman -S nnn`)
- [CRUX portdb](https://crux.nu/portdb/?a=search&q=nnn) (`prt-get depinst nnn`)
- [Debian](https://packages.debian.org/search?keywords=nnn&searchon=names&exact=1) (`apt-get install nnn`)
- [Fedora](https://apps.fedoraproject.org/packages/nnn) (`dnf install nnn`)
- [FreeBSD](https://www.freshports.org/misc/nnn) (`pkg install nnn`)
- [Gentoo](https://packages.gentoo.org/packages/app-misc/nnn) (`emerge nnn`)
- [macOS/Homebrew](http://formulae.brew.sh/formula/nnn) (`brew install nnn`)
- [MacPorts](https://www.macports.org/ports.php?by=name&substr=nnn) (`port install nnn`)
- [Milis Linux](https://notabug.org/milislinux/milis/src/master/talimatname/genel/n/nnn/talimat) (`mps kur nnn`)
- [NixOS](https://github.com/NixOS/nixpkgs/tree/master/pkgs/applications/misc/nnn) (`nix-env -i nnn`)
- [OpenBSD](https://cvsweb.openbsd.org/cgi-bin/cvsweb/ports/sysutils/nnn/) (`pkg_add nnn`)
- [openSUSE](https://software.opensuse.org/package/nnn) (and packages for several other distros) (`zypper in nnn`)
- [pkgrsc](http://pkgsrc.se/sysutils/nnn) (`pkg_add nnn`)
- [Raspbian Testing](https://archive.raspbian.org/raspbian/pool/main/n/nnn/) (`apt-get install nnn`)
- [Slackware](http://slackbuilds.org/repository/14.2/system/nnn/) (`slackpkg install nnn`)
- [Solus](https://packages.getsol.us/shannon/n/nnn/) (`eopkg install nnn`)
- [Source Mage](http://codex.sourcemage.org/test/shell-term-fm/nnn/) (`cast nnn`)
- [Termux](https://github.com/termux/termux-packages/tree/master/packages/nnn) (`pkg in nnn`)
- [Ubuntu](https://packages.ubuntu.com/search?keywords=nnn&searchon=names&exact=1) (`apt-get install nnn`)
- [Void Linux](https://github.com/void-linux/void-packages/tree/master/srcpkgs/nnn) (`xbps-install -S nnn`)

#### Release packages

Packages for Arch Linux, CentOS, Debian, Fedora and Ubuntu are available with the [latest stable release](https://github.com/jarun/nnn/releases/latest).

#### From source

To cook yourself, download the [latest stable release](https://github.com/jarun/nnn/releases/latest) or clone this repository (*risky*). Then install the dependencies and compile (e.g. on Ubuntu 16.04):

    $ sudo apt-get install pkg-config libncursesw5-dev libreadline6-dev
    $ make
    $ sudo make install

`PREFIX` is supported, in case you want to install to a different location.

- Compilation for [Raspberry Pi](https://github.com/jarun/nnn/issues/182)
- Instructions for [Cygwin](https://github.com/jarun/nnn/wiki/Cygwin-instructions)

#### Shell completion

Option completion scripts for Bash, Fish and Zsh can be found in respective subdirectories of [`scripts/auto-completion/`](scripts/auto-completion). Please refer to your shell's manual for installation instructions.

#### QUICKSTART

1. Install the [utilities required](#utility-dependencies) for your regular activities.
2. Configure [cd on quit](https://github.com/jarun/nnn/wiki/hacking-nnn#cd-on-quit).
3. Optionally open all text files in `$EDITOR` (fallback vi): `export NNN_USE_EDITOR=1`
4. Run `n`.
5. To use `nnn` as a GUI app launcher with fuzzy selection menu, drop [`nlaunch`](https://github.com/jarun/nnn/blob/master/scripts/nlaunch/nlaunch) somewhere in your `$PATH`. Note that the launcher requires fzy.
6. Don't memorize keys. Arrows, <kbd>/</kbd> and <kbd>q</kbd> suffice. Press <kbd>?</kbd> for help on keyboard shortcuts anytime.

- For additional functionality [setup plugins](#plugins).
- Visit the wiki page [hacking `nnn`](https://github.com/jarun/nnn/wiki/hacking-nnn) for many more specific use cases.
- To set `nnn` as the default file manager, follow these [instructions](https://github.com/jarun/nnn/wiki/nnn-as-default-file-manager).

#### USAGE

#### Cmdline options

```
usage: nnn [-b key] [-d] [-e] [-i] [-l] [-n]
           [-p file] [-s] [-S] [-v] [-w] [-h] [PATH]

The missing terminal file manager for X.

positional args:
  PATH   start dir [default: current dir]

optional args:
 -b key  open bookmark key
 -d      show hidden files
 -e      use exiftool for media info
 -i      nav-as-you-type mode
 -l      light mode
 -n      use version compare to sort
 -p file selection file (stdout if '-')
 -s      string filters [default: regex]
 -S      du mode
 -v      show version
 -w      wild load
 -h      show help
```

#### Keyboard shortcuts

Press <kbd>?</kbd> in `nnn` to see the list anytime.

```
 NAVIGATION
          ↑ k  Up          PgUp ^U  Scroll up
          ↓ j  Down        PgDn ^D  Scroll down
          ← h  Parent dir  ~ ` @ -  HOME, /, start, last
        ↵ → l  Open file/dir     .  Toggle show hidden
    Home g ^A  First entry    G ^E  Last entry
            /  Filter       Ins ^T  Toggle nav-as-you-type
            b  Pin current dir  ^B  Go to pinned dir
       Tab ^I  Next context      d  Toggle detail view
         , ^/  Leader key  N LeadN  Context N
          Esc  Exit prompt      ^L  Redraw/clear prompt
           ^G  Quit and cd       q  Quit context
         Q ^Q  Quit              ?  Help, config
 FILES
           ^O  Open with...      n  Create new/link
            D  File details     ^R  Rename entry
     ⎵ ^K / Y  Select entry/all  r  Batch rename
         K ^Y  Toggle selection  y  List selection
            P  Copy selection    X  Delete selection
            V  Move selection   ^X  Delete entry
            f  Create archive  m M  Brief/full mediainfo
           ^F  Extract archive   F  List archive
            e  Edit in EDITOR    p  Open in PAGER
 ORDER TOGGLES
           ^J  Disk usage        S  Apparent du
           ^W  Random  s  Size   t  Time modified
 MISC
         ! ^]  Spawn SHELL       C  Execute entry
         R ^V  Pick plugin       L  Lock terminal
            c  SSHFS mount       u  Unmount
           ^P  Prompt  ^N  Note  =  Launcher
```

Note: Help & settings, file details, media info and archive listing are shown in the PAGER. Use the PAGER-specific keys in these screens.

#### Leader key

The Leader key provides a powerful multi-functional navigation mechanism. It is case-sensitive and understands contexts, bookmarks and location shortcuts.

| Key | Function |
|:---:| --- |
| <kbd>1-4</kbd> | Go to/create selected context |
| <kbd>></kbd>, <kbd>.</kbd> | Go to next active context |
| <kbd><</kbd>, <kbd>,</kbd> | Go to previous active context |
| key | Go to bookmarked location |
| <kbd>~</kbd> <kbd>`</kbd> <kbd>@</kbd> <kbd>-</kbd> | Go to HOME, `/`, start, last visited dir |
| <kbd>q</kbd> | Quit context |

#### Contexts

Contexts serve the purpose of exploring multiple directories simultaneously. 4 contexts are available. The status of the contexts are shown in the top left corner:

- the current context is in reverse
- other active contexts are underlined
- rest are inactive

To switch to a context press the Leader key followed by the context number (1-4).

The first time a context is entered, it copies the state of the last visited context. Each context remembers its last visited directory.

When a context is quit, the next active context is selected. If the last active context is quit, the program quits.

##### Context-specific color

Each context can have its own directory color specified:

    export NNN_CONTEXT_COLORS='1234'
colors: 0-black, 1-red, 2-green, 3-yellow, 4-blue (default), 5-magenta, 6-cyan, 7-white

#### Selection

Use <kbd>^K</kbd> to select the file under the cursor.

To select multiple files:

- press <kbd>^Y</kbd> to enter selection mode. In this mode it's possible to
  - cherry-pick individual files one by one by pressing <kbd>^K</kbd> on each entry (works across directories and contexts); or,
  - navigate to another file in the same directory to select a range of files
- press <kbd>^Y</kbd> again to save the selection and exit selection mode.

_NOTE:_ If you are on BSD/macOS, please check the [BSD terminal issue](https://github.com/jarun/nnn#bsd-terminal-issue) with <kbd>^Y</kbd> for workaround.

Selected files are visually indicated by a `+` before the entries.

The selection can now be listed, copied, moved, removed, archived or linked.

Absolute paths of the selected files are copied to the temporary file `~/.config/nnn/.selection`. The path is shown in the help and configuration screen. If `$NNN_COPIER` is set the file paths are also copied to the system clipboard.

#### Filters

Filters support regexes (default) to instantly (search-as-you-type) list the matching entries in the current directory.

Common use cases:
- to list all matches starting with the filter expression, start the expression with a `^` (caret) symbol
- type `\.mkv` to list all MKV files
- use `.*` to match any character (_sort of_ fuzzy search)

There is a program option to filter entries by substring match instead of regex.

#### Navigate-as-you-type

In this mode directories are opened in filter mode, allowing continuous navigation. Works best with the **arrow keys**.

When there's a unique match and it's a directory, `nnn` auto selects the directory and enters it in this mode. To disable this behaviour,

    export NNN_NO_AUTOSELECT=1

This mode takes navigation to the next level when short, unique keypress sequences are possible. For example, to reach `nnn` development directory (located at `~/GitHub/nnn`) from my `$HOME` (which is the default directory the terminal starts in), I use the sequence <kbd>g</kbd><kbd>n</kbd>.

The **_wild load_** option can be extremely handy for users who use this mode constantly. The entries are unsorted when the directory loads. Applying filters sorts the entries (with directories on top). Directory color is disabled in this mode.

#### File indicators

The following indicators are used in the detail view:

| Indicator | File Type |
|:---:| --- |
| `/` | Directory |
| `*` | Executable |
| <code>&#124;</code> | Fifo |
| `=` | Socket |
| `@` | Symbolic Link |
| `@/` | Symbolic Link to directory |
| `b` | Block Device |
| `c` | Character Device |
| `?` | Unknown |

#### Configuration

`nnn` supports the following environment variables for configuration.

| Example `export` | Description |
| --- | --- |
| `NNN_BMS='d:~/Documents;D:~/Docs archive/'` | specify bookmarks (max 10) |
| `NNN_OPENER=mimeopen` | custom file opener |
| `NNN_OPENER_DETACH=1` | do not block when invoking file opener |
| `NNN_CONTEXT_COLORS='1234'` | specify per context color [default: '4444' (all blue)] |
| `NNN_IDLE_TIMEOUT=300` | idle seconds before locking terminal [default: disabled] |
| `NNN_COPIER='/absolute/path/to/copier'` | system clipboard copier script [default: none] |
| `NNN_NOTE=/home/user/Dropbox/notes` | path to note file [default: none] |
| `NNN_TMPFILE=/tmp/nnn` | file to write current open dir path to for cd on quit |
| `NNN_SSHFS_MNT_ROOT=/home/user/.netmnt` | absolute path to SSHFS mount point root |
| `NNN_USE_EDITOR=1` | Open text files in `$EDITOR` (`$VISUAL`, if defined; fallback vi) |
| `NNN_NO_AUTOSELECT=1` | do not auto-select matching dir in _nav-as-you-type_ mode |
| `NNN_RESTRICT_NAV_OPEN=1` | open files on <kbd> ↵</kbd>, not <kbd>→</kbd> or <kbd>l</kbd> |
| `NNN_RESTRICT_0B=1` | do not open 0-byte files |
| `NNN_TRASH=1` | trash files to the desktop Trash [default: delete] |
| `NNN_OPS_PROG=1` | show copy, move progress on Linux |

#### SSHFS mounts

To connect to and mount remote shares using SSHFS, `nnn` requires the following:

1. ssh configuration file `~/.ssh/config` should have the host entries. sshfs reads this file.
2. `$NNN_SSHFS_MNT_ROOT` should be set to the **absolute path** to the directory under which `nnn` creates the mount point for a host. The mount point is the same as the host name.

Example host entry for a Termux environment on Android device:

```
Host phone
    HostName 192.168.0.102
    User u0_a117
    Port 8022
```

If `$NNN_SSHFS_MNT_ROOT` is set to `/home/user/remotes`, the above host `phone` will be mounted at `/home/user/remotes/phone`. `nnn` creates the directory `phone` if it doesn't exist.

To unmount a mount point highlight it in `nnn` (so that it's the current entry) and press the relevant keybind to unmount. It might be a good idea to bookmark `$NNN_SSHFS_MNT_ROOT`.

Notes:

1. `nnn` places you inside the mount point after a successful (un)mount so you can ensure the operation completed successfully indeed. To jump back to the last directory, press the usual <kbd>-</kbd>.
2. `nnn` doesn't delete the mount point on unmount to prevent accidental data loss.
3. More information on [SSHFS](https://wiki.archlinux.org/index.php/SSHFS).

#### Help

    $ nnn -h
    $ man nnn
To lookup keyboard shortcuts at runtime, press <kbd>?</kbd>.

#### PLUGINS

To extend the capabilities of `nnn`, plugins are introduced. Plugins are scripts which `nnn` can communicate with and trigger. This mechanism fits perfectly with the fundamental design to keep the core file manager lean and fast, by delegating repetitive (but not necessarily file manager-specific) tasks to the plugins.

Copy the [plugins](https://github.com/jarun/nnn/tree/master/plugins) of your interest to `~/.config/nnn/plugins`.

Use the pick plugin shortcut to visit the plugin directory and execute a plugin. Repeating the same shortcut cancels the operation and puts you back in the original directory.

If you have an interesting plugin feel free to raise a PR.

#### TROUBLESHOOTING

##### Tmux configuration

`nnn` might not handle keypresses correctly when used with tmux (see issue #104 for more details). Set `TERM=xterm-256color` to address it.

##### BSD terminal issue

TLDR: Use the keybind <kbd>K</kbd> to toggle selection if you are having issues with <kbd>^Y</kbd>.

By default in OpenBSD & FreeBSD (and probably on macOS as well), `stty` maps <kbd>^Y</kbd> to `DSUSP`. This means that typing <kbd>^Y</kbd> will suspend `nnn` as if you typed <kbd>^Z</kbd> (you can bring `nnn` back to the foreground by issuing `fg`) instead of entering multi-selection mode. You can check this with `stty -a`. If it includes the text `dsusp = ^Y`, issuing `stty dsusp undef` will disable this `DSUSP` and let `nnn` receive the <kbd>^Y</kbd> instead.

##### Restrict file open

In order to disable opening files on accidental navigation key (<kbd>→</kbd> or <kbd>l</kbd>) press:

    export NNN_RESTRICT_NAV_OPEN=1

Use <kbd>Enter</kbd> to open these files.

##### Restrict 0-byte files

Restrict opening 0-byte files due to [unexpected behaviour](https://github.com/jarun/nnn/issues/187); use _edit_ or _open with_ to open the file.

    export NNN_RESTRICT_0B=1

#### WHY FORK?

`nnn` was initially forked from [noice](http://git.2f30.org/noice/) but is significantly [different](https://github.com/jarun/nnn/wiki/nnn-vs.-noice) today. I chose to fork because:
- one can argue my approach deviates from the goal of the original project -  keep the utility `suckless`. `noice` was rudimentary. In my opinion evolution is the taste of time.
- I would like to have a bit of control on what features are added in the name of desktop integration. A feature-bloat is the last thing in my mind. Check out [nnn design considerations](https://github.com/jarun/nnn/wiki/nnn-design-considerations) for more details.

Trivia: The name `nnn` stands for _Noice is Not Noice, a noicer fork..._.

#### MENTIONS

- [FOSSMint](https://www.fossmint.com/nnn-linux-terminal-file-browser/)
- [Hacker News](https://news.ycombinator.com/item?id=18520898)
- [It's FOSS](https://itsfoss.com/nnn-file-browser-linux/)
- [LinuxLinks1](https://www.linuxlinks.com/nnn-fast-and-flexible-file-manager/)
- [LinuxLinks2](https://www.linuxlinks.com/bestconsolefilemanagers/)
- [Suckless Rocks](https://suckless.org/rocks/)
- [Ubuntu Full Circle Magazine - Issue 135](https://fullcirclemagazine.org/issue-135/)

#### DEVELOPERS

1. Copyright © 2014-2016 Lazaros Koromilas
2. Copyright © 2014-2016 Dimitris Papastamos
3. Copyright © 2016-2019 [Arun Prakash Jana](https://github.com/jarun)

Contributions are welcome. Please visit the [ToDo list](https://github.com/jarun/nnn/issues/213).

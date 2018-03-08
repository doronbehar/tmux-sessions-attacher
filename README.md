# Tmux Sessions Attacher

This project strives to address a task many tmux users execute regularly and it is attaching to existing tmux sessions on remote / local machines - like Virtual Private Servers and other animals.

## Installation

- For Arch Linux Users: Install the AUR package: [`tmux-session-attacher`](https://aur.archlinux.org/packages/tmux-session-attacher).

- For everyone else: Just put the script in your `$PATH`, you know the drill. It's recommended to add the desktop entry file included in this repository ([`tmux-session-attacher.desktop`](tmux-session-attacher.desktop)) to your applications directory as well. Usually it means putting it in `~/.local/share/applications/` and running `update-desktop-database ~/.local/share/applications` is enough.

## Usage

Basically, the script is pretty simple, it reads a configuration file and searches on your servers for running tmux sessions and it prompts you for attaching them to a running terminal emulator. It uses (by default) non login shells inside the terminal emulator which gives a much smoother experience of attaching and detaching.

### Configuration

The configuration file looks like this:

```yml
general:
    terminal-emulator: "urxvt" # if not defined, the script will do his job inside the current tty. Configuration can be overridden with `-T|--terminal-emulator no` or `-t|--terminal-emulator string`
    ssh-options: "" # options to pass to ssh
    tmux-options: "" # options to pass to tmux
    
hosts:
    - "myvps.vpsprovider.net"
    - "myhomeserver"
    - "myraspberrypi"
```

That's all there is to it, host specific options can be set with ssh configuration.

### Running

Basically you can run it either from a command prompt and the script will fork itself or you can put it in a `.desktop` file and run it from your desktop environment. Here is an example [`tmux-session-attacher.desktop`](tmux-session-attacher.desktop):

```desktop
[Desktop Entry]
Type=Application
Name=SSH Remote Tmux Session Manager
Exec=tmux-session-attacher
Keywords=shell;prompt;commandline;
Comment=Interactivly choose a Tmux session to attach on configured remote machines
Icon=utilities-terminal
Terminal=false
Categories=Utility;
MimeType=
```


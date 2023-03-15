
```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}

Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineOption -Colors @{ InLinePrediction = '#00cc00'
                                Command            = 'Magenta'
                                Number             = 'White'
                                Member             = 'Yellow'
                                Operator           = 'Yellow'
                                Type               = 'Green'
                                Variable           = 'Green'
                                Parameter          = 'Yellow'
                                ContinuationPrompt = 'White'
                                Default            = 'White'
                              }
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete
Set-PSReadLineKeyHandler -Key F1 -Function ShowCommandHelp 

function dwr ($url){
    Invoke-WebRequest $url -OutFile $url.split("/")[-1]
}
```

# Tmux using WSL
[source](https://superuser.com/questions/408874/tmux-screen-alternative-for-powershell)
Although it wasn't possible when this question was originally asked, with Windows Subsystem for Linux, it's now possible to use a "real" tmux to manage PowerShell windows.

### Short-version
In a WSL instance with tmux installed, set up your ~/.tmux.conf with:
```shell

set -g default-command "cd $(pwsh.exe -c 'Write-Host -NoNewLine \$env:userprofile' | xargs -0 wslpath); exec pwsh.exe --nologo"
set-window-option -g automatic-rename off
bind c new-window -n "PowerShell"
```

### Benefits and Features
Most of the features you'd normally expect from tmux, including:

- Full (?) hotkeys support
- Scrollback / Copy mode for PowerShell
And many more
### Limitations
If the original session is disconnected, re-attaching will result in a broken pipe. However, you can attach multiple clients at once, as long as the original remains open.
More details
There are several ways to set this up, but here's how I'm doing it at the moment:

Install Windows Subsystem for Linux. You don't have to enable WSL2; just WSL v1 will work fine for this (and perhaps better than WSL2).

Install the Alpine Linux distribution. I use this as the base for the tmux feature, since it has very low overhead (less than 12MB, including tmux).

The next few steps are optional. I create a new, cloned WSL instance for PowerShell tmux. You could just use the default Alpine instance, but I like to have single-purpose WSL instances, similar to Docker containers.

```shell
mkdir $env:userprofile\Documents\WSL\instances # Or wherever you want to set this up
mkdir $env:userprofile\Documents\WSL\images
cd $env:userprofile\Documents\WSL
wsl --export Alpine .\images\alpine_base.tar
mkdir .\instances\posh_tmux
wsl --import posh_tmux .\instances\posh_tmux .\images\alpine_base.tar --version 1 
Launch the WSL instance as root with wsl -d posh_tmux -u root

adduser tmux, and give it a password.

Set the default user for the instance by creating /etc/wsl.conf with the following contents:

[user]
default = tmux
apk add tmux to install tmux

Exit the session, relaunch with wsl ~ -d tmux (omitting the username, since it will now default to the tmux user)

Create a ~/.tmux.conf with the following:

set -g default-command "cd $(pwsh.exe -c 'Write-Host -NoNewLine \$env:userprofile' | xargs -0 wslpath); exec pwsh.exe --nologo"
set-window-option -g automatic-rename off
bind c new-window -n "PowerShell"

# Give this tmux a "PowerShell blue" color to differentiate it
set -g status-bg blue

# Use UTF8
set -qg utf8
set-window-option -qg utf8 on

# Recommended, to avoid the Ctrl+B finger-gymnastics
# Change default prefix to Screen's
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix
bind-key -n C-b send-prefix
bind C-a last-window

# Optional
# split panes using - and |
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

set -g history-limit 10000

set -g default-terminal "screen-256color"
Create a ~/.profile with the following:

if tmux has-session -t=posh; then
  exec tmux attach-session -t posh
else
  exec tmux new-session -s posh -n PowerShell
fi
```
Set up a PowerShell Core tmux profile in Windows Terminal, ConEmu, or however you prefer. The launch command is simply `wsl -d tmux_posh
If you need to access the instance without entering tmux/PowerShell (for instance, to sudo apk upgrade or to edit the config), launch instead with 
```shell
wsl ~ -d tmux_posh -e sh (or wsl ~ -d tmux_posh -u root).
```


You can access tmux commands from within PowerShell by `wsl -d tmux_posh -e tmux` <tmux_command. For instance, `wsl -d tmux_posh -e tmux rename-window host1`. 

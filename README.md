# dotfiles-windows

# Initial Setup

## Git
<https://git-scm.com/download>

1. Install git for windows (x64) from that link
2. Make sure in the options to select `Override the Branch Names` (let it use main) and `Git from the command line and also 3rd party software`. The rest of the defaults are fine.

## Chocolatey
<https://chocolatey.org/install>

1. From Admin Terminal: `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`

## Windows Terminal

1. Install Windows Terminal from Microsoft Store

### Powershell 7
1. In windows terminal, click the down arrow next to the tabs
2. Click Settings
3. Select `PowerShell` as default profile (not `Windows PowerShell`)
4. Relaunch Windows Terminal

#### Upgrading PowerShell 7 from Command Line

`iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"`

### Oh-My-Posh
<https://ohmyposh.dev/docs/windows>

<https://www.hanselman.com/blog/my-ultimate-powershell-prompt-with-oh-my-posh-and-the-windows-terminal>

<https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/CascadiaCode.zip?WT.mc_id=-blog-scottha>

<https://gist.github.com/kallookoo/14005653bcb6d9b7e6b70a7f8fcf6807>

1. Download and install Cascadia Code Nerd Fonts from the link above
2. Select `CascaydiaCode NF` from the `Powershell` profile Appearance tab in Windows Terminal settings
3. Install oh-my-posh `winget install JanDeDobbeleer.OhMyPosh`
4. Restart Windows Terminal
5. `cp %LOCALAPPDATA%\Programs\oh-my-posh\themes\half-life.omp.json ~\half-life.omp.json`
5. `code $PROFILE`
6. Add the following lines:
      ```
      oh-my-posh --init --shell pwsh --config ~/half-life.omp.json | Invoke-Expression
      Import-Module -Name Terminal-Icons
      ```
7. `Install-Module -Name Terminal-Icons -Repository PSGallery`
8. `. $PROFILE`
9. Copy the Raw text of the Tomorrow Night theme from the link above
10. From Windows Terminal Settings, Open JSON file
11. Scroll down to the `schemes` section and paste in the Tomorrow Night theme, making sure to add a trailing comma (unless it's the last one in the list)
12. Save the file and close
13. Restart terminal, should be a Lambda terminal icon now with much nicer text colors.

### CMDER
<https://medium.com/talpor/windows-terminal-cmder-%EF%B8%8F-573e6890d143>

## VS Code
1. From admin terminal: `choco install code`
1. Color Scheme "tomorrow night eighties"

## pyenv-win
<https://github.com/pyenv-win/pyenv-win>

1. From Admin Terminal: `choco install pyenv-win`
2. Open non-admin terminal
3. `pyenv --version`
3. `pyenv --versions`
4. `pyenv install 3.10.1` (or whatever is latest)
5. Restart terminal
6. `pyenv global 3.10.1`
8. `pyenv rehash`

## MPV

1. From admin terminal: `choco install mpv`
2. Open non-admin terminal
3. `code %APPDATA%\mpv\input.conf`
4. Add:
      ```
      WHEEL_UP add volume 5
      WHEEL_DOWN add volume 5
      ```
5. Save and close

## Streamlink

1. Open non-admin terminal
2. `pip install streamlink`
3. `pyenv rehash`
4. Run `streamlink`
5. `code %APPDATA%\streamlink\config`
6. Add:
      ```
      # Player options
      player=mpv --cache 2048
      player-no-close
      ```
7. Save and close
7. `streamlink twitch.tv/gamesdonequick best`

## Docker
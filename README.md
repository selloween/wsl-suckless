# wsl-suckless

A short setup guide of making WSL more awesome. 

## WSL Terminal
Download and install WSL Terminal: https://github.com/goreliu/wsl-terminal

```
wget https://github.com/goreliu/wsl-terminal/releases/download/v0.8.13/wsl-terminal-0.8.13.7z && 7z x wsl-terminal-0.8.13.7z
```

## Use TMUX

### Start TMUX on launching a terminal
Add this to `~/.bashrc`

```
[[ -z "$TMUX" && -n "$USE_TMUX" ]] && {
    [[ -n "$ATTACH_ONLY" ]] && {
        tmux a 2>/dev/null || {
            cd && exec tmux
        }
        exit
    }

    tmux new-window -c "$PWD" 2>/dev/null && exec tmux a
    exec tmux
}
```

## Install ZSH
```
sudo apt-get install zsh
```

### Make ZSH the default shell
Add this to .bashrc
```
# Launch Zsh
if [ -t 1 ]; then
exec zsh
fi
```

## Install "Oh My ZSH"
```
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

## Set ZSH Theme
https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

Set e.g. `ZSH_THEME="agnoster" ` in ~/.zshrc`

## Add Solarized Dark Colors
In theme options of WSL Terminal choose the Solarized Dark theme.

### Get terminal colors for Solarized Dark.
```
mkdir ~/git
cd ~/git
git clone https://github.com/seebi/dircolors-solarized .
echo "eval 'dircolors ~/Git/dircolors-solarized/dircolors.256dark'" >> ~/.zshrc
```
## Download and install DejaVu Font

https://github.com/powerline/fonts/tree/master/DejaVuSansMono

Change Font in WSL Terminal Settings.

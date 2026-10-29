# mydotfiles

Personal dotfiles for macOS.

## Layout

| Path | Purpose | Installs to |
| --- | --- | --- |
| `.zshrc` | Zsh config (oh-my-zsh, prompt handled by Starship) | `~/.zshrc` |
| `.config/starship.toml` | Starship prompt, Catppuccin Mocha theme | `~/.config/starship.toml` |
| `iterm2/DynamicProfiles/catppuccin-mocha.json` | iTerm2 profile, Catppuccin Mocha | `~/Library/Application Support/iTerm2/DynamicProfiles/` |
| `vscode/settings.json` | VS Code user settings | `~/Library/Application Support/Code/User/settings.json` |
| `mac/Brewfile` | Homebrew taps, formulae, casks and Go tools | n/a |
| `legacy/.p10k.zsh` | Old Powerlevel10k config, kept for reference | n/a |

## Setup on a new Mac

```sh
# Homebrew packages
brew bundle install --file=mac/Brewfile

# Config files
cp .zshrc ~/.zshrc
mkdir -p ~/.config && cp .config/starship.toml ~/.config/starship.toml
cp iterm2/DynamicProfiles/catppuccin-mocha.json ~/Library/Application\ Support/iTerm2/DynamicProfiles/
cp vscode/settings.json ~/Library/Application\ Support/Code/User/settings.json
```

`.zshrc` expects oh-my-zsh at `~/.oh-my-zsh`.

## Updating the Brewfile

```sh
brew bundle dump --file=mac/Brewfile --force --no-describe
```

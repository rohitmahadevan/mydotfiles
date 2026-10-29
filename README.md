# mydotfiles

Personal dotfiles for macOS, managed with [chezmoi](https://www.chezmoi.io).

## Layout

`.chezmoiroot` points chezmoi at `home/`, so only files under `home/` are installed. Everything else in the repo is ignored by chezmoi.

| Path | Installs to |
| --- | --- |
| `home/dot_zshrc` | `~/.zshrc` (oh-my-zsh, prompt handled by Starship) |
| `home/private_dot_config/starship.toml` | `~/.config/starship.toml` (Catppuccin Mocha) |
| `home/private_Library/private_Application Support/iTerm2/DynamicProfiles/catppuccin-mocha.json` | iTerm2 dynamic profile |
| `home/private_Library/private_Application Support/private_Code/User/settings.json` | VS Code user settings |
| `home/.chezmoiscripts/run_onchange_install-packages.sh.tmpl` | Runs `brew bundle install --no-upgrade` whenever `mac/Brewfile` changes (installs missing packages, skips upgrading outdated ones) |
| `mac/Brewfile` | Homebrew taps, formulae, casks and Go tools |
| `legacy/.p10k.zsh` | Old Powerlevel10k config, kept for reference |

The `dot_` prefix maps to a leading `.` and `private_` keeps the target at `0700`/`0600` permissions.

## Setup on a new Mac

```sh
# Install Homebrew first, then:
brew install chezmoi
chezmoi init --apply rohitmahadevan/mydotfiles
```

This clones the repo to `~/.local/share/chezmoi`, installs the config files and runs `brew bundle install --no-upgrade`. `.zshrc` expects oh-my-zsh at `~/.oh-my-zsh`.

To keep the repo at `~/github/mydotfiles` instead, clone it there and add to `~/.config/chezmoi/chezmoi.toml`:

```toml
sourceDir = "~/github/mydotfiles"
```

## Day-to-day

```sh
chezmoi diff               # what apply would change in $HOME
chezmoi apply              # write repo state to $HOME
chezmoi re-add             # pull edits made in $HOME back into the repo
chezmoi add ~/.some/file   # start managing a new file
chezmoi cd                 # open a shell in the repo
```

## Updating the Brewfile

```sh
brew bundle dump --file=mac/Brewfile --force --no-describe
```

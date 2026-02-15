# My Dev Environment

A template [Cygnet](https://github.com/YB-BigSwan/cygnet) bootstrap repo for setting up a development workstation.

## Supported Platforms

- **macOS** — Homebrew (formulae + casks)
- **Linux** — apt-get
- **Windows** — Chocolatey

## Usage

1. Download and install [Cygnet](https://github.com/YB-BigSwan/cygnet)
2. Paste this repo's URL into Cygnet
3. Click Start

Cygnet reads `manifest.json`, detects your platform, and runs only the steps that apply.

## Structure

```
manifest.json                   # Declares the setup steps (the engine reads this)
packages/
  brewfile.txt                  # macOS CLI formulae (Homebrew)
  casks.txt                     # macOS GUI applications (Homebrew Cask)
  apt-packages.txt              # Linux CLI packages (apt-get)
  apt-gui.txt                   # Linux GUI packages (apt-get)
  choco-packages.txt            # Windows CLI packages (Chocolatey)
  choco-gui.txt                 # Windows GUI packages (Chocolatey)
vscode-extensions.txt           # VS Code extension IDs (all platforms)
dotfiles/                       # Dotfiles symlinked to $HOME
  .zshrc
app-config/                     # Application config files
  vscode/settings.json          # Copied to VS Code's settings path
  iterm2/                       # Add iTerm2 profiles here
```

## Customizing

- Edit `manifest.json` to add, remove, or reorder steps
- Edit the package lists under `packages/` for each platform
- VS Code extensions and dotfiles are cross-platform by default
- Put your dotfiles in `dotfiles/` — they'll be symlinked to `$HOME`
- Add app config files under `app-config/` and map them in the manifest

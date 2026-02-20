# My Dev Environment

A template [Cygnet](https://github.com/YB-BigSwan/cygnet) bootstrap repo for setting up a development workstation.

## Supported Platforms

- **macOS** — Homebrew (formulae + casks)
- **Linux** — apt-get
- **Windows** — Chocolatey

## What Gets Installed

| Category | macOS | Linux | Windows |
|----------|-------|-------|---------|
| CLI tools | Homebrew formulae | apt packages | Chocolatey packages |
| GUI apps | Homebrew casks | apt packages | Chocolatey packages |
| Shell | Oh My Zsh + plugins | Oh My Zsh + plugins | — |
| Dotfiles | Symlinked to `$HOME` | Symlinked to `$HOME` | Symlinked to `$HOME` |
| VS Code | Extensions + settings | Extensions + settings | Extensions + settings |
| JetBrains | IntelliJ IDEA + plugins | IntelliJ IDEA + plugins | IntelliJ IDEA + plugins |

## Usage

1. Download and install [Cygnet](https://github.com/YB-BigSwan/cygnet)
2. Paste this repo's URL into Cygnet
3. Click Start

Cygnet reads `manifest.json`, detects your platform, and runs only the steps that apply.

## Structure

```
manifest.json                       # Declares the setup steps (the engine reads this)
packages/
  brewfile.txt                      # macOS CLI formulae (Homebrew)
  casks.txt                         # macOS GUI applications (Homebrew Cask)
  apt-packages.txt                  # Linux CLI packages (apt-get)
  apt-gui.txt                       # Linux GUI packages (apt-get)
  choco-packages.txt                # Windows CLI packages (Chocolatey)
  choco-gui.txt                     # Windows GUI packages (Chocolatey)
extensions/
  vscode.txt                        # VS Code extension IDs (all platforms)
  jetbrains.txt                     # JetBrains plugin IDs (all platforms)
dotfiles/                           # Dotfiles symlinked to $HOME
  .zshrc
app-config/                         # Application config files
  vscode/settings.json              # Copied to VS Code's settings path
  iterm2/                           # Add iTerm2 profiles here
```

## Step Types

Cygnet supports the following manifest step types:

| Type | Description |
|------|-------------|
| `packages` | Install CLI or GUI packages via the platform's package manager |
| `shell` | Install a shell framework (Oh My Zsh) and plugins |
| `dotfiles` | Symlink or copy dotfiles to `$HOME` |
| `vscode-extensions` | Install VS Code extensions from a list file |
| `jetbrains-plugins` | Install JetBrains IDE plugins from a list file |
| `config-files` | Copy application config files to their platform-specific paths |
| `script` | Run a custom shell script |

## Customizing

- Edit `manifest.json` to add, remove, or reorder steps
- Edit the package lists under `packages/` for each platform
- Add or remove extensions in `extensions/vscode.txt` and `extensions/jetbrains.txt`
- Put your dotfiles in `dotfiles/` — they'll be symlinked to `$HOME`
- Add app config files under `app-config/` and map them in the manifest
- Each step can be scoped to specific platforms with the `"platform"` field

### JetBrains Plugins

The `jetbrains-plugins` step requires an `"ide"` field in its config to specify which IDE to install plugins for. Supported IDEs: `idea`, `webstorm`, `pycharm`, `goland`, `phpstorm`, `rider`, `clion`, `datagrip`, `rustrover`.

Plugin IDs are the XML Plugin ID found on each plugin's [JetBrains Marketplace](https://plugins.jetbrains.com/) page under "Additional Information". The IDE's CLI launcher must be on your `PATH` (enable this in JetBrains Toolbox settings or add the IDE's `bin/` directory manually).

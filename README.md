# 🧰 macOS Setup with Homebrew

A simple, scriptable setup for macOS using [Homebrew](https://brew.sh/).

This repo contains a `Brewfile` that installs all essential apps, CLI tools, and developer utilities for a clean and productive environment. Perfect for setting up a new Mac or keeping your current setup synchronized.

> **Note**: This setup works on both Intel and Apple Silicon Macs. Homebrew will install to `/opt/homebrew` on Apple Silicon and `/usr/local` on Intel.

## 📦 What Gets Installed

This Brewfile includes carefully selected tools for development and productivity. View the complete list:

- [View Brewfile](./Brewfile) in this repo
- Or preview it directly:
  ```bash
  curl -s https://raw.githubusercontent.com/mlevit/homebrew/main/Brewfile
  ```

## 🚀 Getting Started

### 1. Install Homebrew

If you don't have Homebrew installed yet, run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then add Homebrew to your shell profile (if not automatically done):

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### 2. Install Everything

```bash
brew bundle --file=<(curl -s https://raw.githubusercontent.com/mlevit/homebrew/main/Brewfile)
```

### 3. Verify Installation

Check what was installed:

```bash
brew list           # CLI tools
brew list --cask    # Desktop applications
```

## 🧹 Maintenance

Keep everything up to date with:

```bash
brew update && brew upgrade
```

To remove unused packages and free up disk space:

```bash
brew cleanup
```

Check for potential issues:

```bash
brew doctor
```

## 🧩 Customizing Your Setup

### Modify the Brewfile

Add or remove apps from the `Brewfile` as needed. The syntax is simple:

```ruby
# CLI tools
brew "git"
brew "node"

# Desktop applications
cask "visual-studio-code"
cask "google-chrome"

# Mac App Store apps (requires mas-cli)
mas "Xcode", id: 497799835
```

### Export Your Current Setup

Create a Brewfile from your current environment:

```bash
brew bundle dump --describe --file=Brewfile
```

This updates your `Brewfile` to match everything currently installed.

## 🔧 Troubleshooting

**Permission errors**

```bash
sudo chown -R $(whoami) /usr/local/* /opt/homebrew/*
```

**Command not found after installation**

- Restart your terminal, or
- Run `source ~/.zprofile` (or `~/.bash_profile` for bash)

**Homebrew not in PATH**

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
source ~/.zprofile
```

**Installation fails partway through**

```bash
brew bundle cleanup  # Remove installed packages
brew bundle          # Try again
```

## 🧠 How It Works

- `brew install` manages command-line tools and utilities
- `brew install --cask` manages desktop applications
- `mas` (Mac App Store CLI) can install App Store applications
- Everything can be reinstalled on a new Mac in minutes using this repo

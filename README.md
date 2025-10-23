# 🧰 macOS Setup with Homebrew

A simple, scriptable setup for macOS using [Homebrew](https://brew.sh/).

This repo includes a `Brewfile` that installs all essential apps, CLI tools, and developer utilities for a clean and productive environment.

## 🚀 Getting Started

### 1. Install Homebrew

If you don’t have Homebrew installed yet, run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then add Homebrew to your shell profile (if not automatically done):

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### 2. Install everything

```bash
brew bundle --file=<(curl -s https://raw.githubusercontent.com/mlevit/homebrew/main/Brewfile)
```

### 4. Verify installation

```bash
brew list
brew list --cask
```

## 🧹 Maintenance

Keep everything up to date with:

```bash
brew update && brew upgrade
```

To remove unused packages:

```bash
brew cleanup
```

## 🧩 Customizing

Add or remove apps from the `Brewfile` as needed.
You can also export your current setup with:

```bash
brew bundle dump --describe --file=Brewfile
```

This updates your `Brewfile` to match your current environment.

## 🧠 Notes

- `brew` manages CLI tools
- `brew install --cask` manages desktop apps
- Everything can be reinstalled on a new Mac in minutes using this repo

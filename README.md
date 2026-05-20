# cleanmac

Interactive Mac cleanup tool for developers. Free up disk space without breaking your dev environment.

## Install

```bash
brew install mosayyyed/cleanmac/cleanmac
```

## Usage

```bash
cleanmac          # interactive — pick what to clean
cleanmac --dev    # dev-safe — build artifacts only (env untouched)
cleanmac --update # update to latest version
```

### Interactive mode

Launches a multi-select menu showing each cache category with its current size.
Use `TAB` to toggle items, `CTRL-A` to select all, `ENTER` to confirm.

### Dev-safe mode (`--dev`)

Cleans only build artifacts. Safe to run anytime without re-setting up your environment.

| Cleaned | Not touched |
|---|---|
| Gradle caches | `~/.gradle/wrapper` |
| Android build cache | `~/.pub-cache` (Flutter) |
| Xcode DerivedData | `~/.cocoapods` (specs) |
| Xcode Archives | iOS Simulators |
| Project `build/` folders | `node_modules` |
| npm / VS Code cache | Android SDK |

## Requirements

- macOS
- [fzf](https://github.com/junegunn/fzf) (installed automatically with Homebrew)

# cleanmac

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

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
cleanmac --version
```

### Interactive mode

Launches a multi-select menu showing each cache category with its current size.
Use `TAB` to toggle items, `CTRL-A` to select all, `ENTER` to confirm.

Only caches are listed. `~/Library/Containers` and `~/Library/Group Containers` are
never offered — they hold real app data (WhatsApp, Telegram, Notes, ...).
Items that are slow to get back are labelled, e.g. Xcode Archives (dSYMs, not regenerable)
or the Codex runtime and Shorebird engine (re-download on next use).

### Dev-safe mode (`--dev`)

Cleans only build artifacts. Safe to run anytime without re-setting up your environment.

| Cleaned | Not touched |
|---|---|
| Gradle caches | `~/.gradle/wrapper` |
| Android build cache | `~/.pub-cache` (Flutter) |
| Xcode DerivedData, IB Support, Previews | `~/.cocoapods` (specs) |
| Project `build/`, `.dart_tool`, `Pods`, `.gradle` | iOS Simulator data |
| Old Android NDK versions (keeps Flutter's default + newest) | Xcode Archives |
| npm / VS Code / CocoaPods / uv / puppeteer caches | Flutter SDK, Codex runtime, Shorebird engine |
| Unavailable simulators, `brew cleanup` | `node_modules` |

Project folders are scanned under `~/AndroidStudioProjects`, `~/StudioProjects`, `~/DEV`,
`~/Development`, `~/Desktop`, `~/Projects` and `~/Documents`, and only next to a project
file (`pubspec.yaml`, `Podfile`, `build.gradle`).

## Requirements

- macOS
- [fzf](https://github.com/junegunn/fzf) (installed automatically with Homebrew)

# MY CONFIG SHIT

Collection of settings and instructions to set up a new **macOS** machine

## Setting up

### Set up [macOS](https://macos-defaults.com/)

```sh
defaults write com.apple.dock "orientation" -string "left" && killall Dock
defaults write com.apple.dock "tilesize" -int "40" && killall Dock
defaults write com.apple.dock "show-recents" -bool "false" && killall Dock
defaults write com.apple.finder "AppleShowAllFiles" -bool "true" && killall Finder
defaults write NSGlobalDomain "AppleShowAllExtensions" -bool "true" && killall Finder
defaults write com.apple.finder "FXRemoveOldTrashItems" -bool "true" && killall Finder
```

### <img src="https://cdn.svgporn.com/logos/homebrew.svg" align=left height="24" alt="homebrew" /> Set up [Homebrew](https://brew.sh) as package manager

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Install [Fish](https://fishshell.com) and [Ghostty](https://ghostty.org/), then download SF Mono

```sh
brew install fish ghostty font-sf-mono
```

### Set up [Fisher](https://github.com/jorgebucaran/fisher) as plugin manager for Fish

```sh
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

### Install [Tide](https://github.com/IlanCosman/tide) as shell prompt with [Fisher](https://github.com/jorgebucaran/fisher)

```sh
fisher install IlanCosman/tide@v6
```

#### Configure Tide

```fish
tide configure --auto --style=Classic --prompt_colors='True color' --classic_prompt_color=Dark --show_time='12-hour format' --classic_prompt_separators=Angled --powerline_prompt_heads=Round --powerline_prompt_tails=Round --powerline_prompt_style='Two lines, character and frame' --prompt_connection=Dotted --powerline_right_prompt_frame=No --prompt_connection_andor_frame_color=Lightest --prompt_spacing=Sparse --icons='Many icons' --transient=Yes
```

```fish
set -U tide_node_icon "󰎙"
set -U tide_node_color "5FA04E"
set -U tide_bun_icon ""
set -U tide_bun_color "FBF0DF"
set -U tide_git_icon ""
set -U tide_cmd_duration_decimals 3
set -U tide_cmd_duration_threshold 0
```

### <img src="https://cdn.svgporn.com/logos/visual-studio-code.svg" align=left height="24" alt="visual-studio-code" /> Install [Visual Studio Code](https://code.visualstudio.com)

```sh
brew install visual-studio-code
```

### <img src="https://cdn.svgporn.com/logos/git-icon.svg" align=left height="24" alt="git" /> Install [Git](https://git-scm.com)

```sh
brew install git
```

#### Configure git

```sh
git config --global user.name "Jasper 張"
git config --global user.email "jaspertzj@outlook.sg"
git config --global core.editor "code --wait"
```

### Install other software

```sh
brew install 1password microsoft-edge@dev firefox@developer-edition raycast macs-fan-control rectangle keka cloudflare-warp iina fastfetch btop
brew install kekaexternalhelper
```

#### <img src="https://cdn.svgporn.com/logos/docker-icon.svg" align=left height="24" alt="docker" /> [OrbStack](https://orbstack.dev) (Docker Desktop Alternative)

```sh
brew install orbstack
```

## Environment configs

### <img src="https://cdn.svgporn.com/logos/nodejs-icon.svg" align=left height="24" alt="node-js" /> [Node](https://nodejs.org) Environment

#### Install [pnpm](https://pnpm.io/)

```sh
curl -fsSL https://get.pnpm.io/install.sh | sh -
```

#### Set up autocomplete

```sh
pnpm completion fish > ~/.config/fish/completions/pnpm.fish
```

#### Install Node versions

```sh
# Current
pnpm env use --global latest
# LTS
pnpm env use --global lts
```

### <img src="https://cdn.svgporn.com/logos/bun.svg" align=left height="24" alt="node-js" /> [Bun](https://bun.sh) Environment

#### Install Bun

```sh
curl -fsSL https://bun.sh/install | bash
```

### <img src="https://cdn.svgporn.com/logos/python.svg" align=left height="24" alt="python" /> [Python](https://www.python.org) Environment

#### Install [pyenv](https://github.com/pyenv/pyenv)

```sh
brew install pyenv
```

#### Set up shell environment

```fish
set -Ux PYENV_ROOT $HOME/.pyenv
fish_add_path $PYENV_ROOT/bin
```

> [!IMPORTANT]
> Add to `~/.config/fish/config.fish`

```fish
pyenv init - | source
```

#### Install Python versions

```sh
# Example
pyenv install 3.13-dev
```

#### Set Python version

```sh
# Set Global Default
pyenv global 3.13-dev
# Project Specific
pyenv local 3.13-dev
# Virtual Environment
python3 -m venv .venv
source .venv/bin/activate.fish
```

### <img src="https://cdn.svgporn.com/logos/ruby.svg" align=left height="24" alt="ruby" /> [Ruby](https://www.ruby-lang.org) Environment

#### Install [rbenv](https://github.com/rbenv/rbenv)

```sh
brew install rbenv
```

#### Install Ruby versions

```sh
# Example
rbenv install 3.3-dev
```

#### Set Ruby version

```sh
# Set Global Default
rbenv global 3.3-dev
# Project Specific
rbenv local 3.3-dev
```

#### Install Cocoapods

```sh
gem install cocoapods
```

### <img src="https://cdn.svgporn.com/logos/rust.svg" align=left height="24" alt="rust" /> [Rust](https://www.rust-lang.org) Environment

#### Install [rustup](https://github.com/rust-lang/rustup)

```sh
brew install rustup
rustup default stable
```

### <img src="https://cdn.svgporn.com/logos/react.svg" align=left height="24" alt="react" icon="react" /> [React Native](https://reactnative.dev) Environment

#### Install [Xcode](https://developer.apple.com/xcode), [Android Studio](https://developer.android.com/studio), [Watchman](https://github.com/facebook/watchman) and Azul Zulu Java

> [!NOTE]
> Use App Store to install **Xcode**

```sh
brew install watchman zulu@17 android-studio
```

#### Set up Android Studio for React Native Development

Use the SDK Manager in Android Studio to install the following SDK Tools:

- Android SDK Platform
- Android SDK Platform-Tools
- Android SDK Build-Tools
- Android Emulator

> [!IMPORTANT]
> Add to `~/.config/fish/config.fish`

```fish
set -x JAVA_HOME_REACT_NATIVE /Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home
set -x ANDROID_HOME $HOME/Library/Android/sdk
set -x PATH $PATH $ANDROID_HOME/emulator
set -x PATH $PATH $ANDROID_HOME/platform-tools
```

> [!WARNING]
> Verify the path of `ANDROID_HOME` is correct

#### Set `JAVA_HOME` environment variable for React Native

```fish
set -x JAVA_HOME $JAVA_HOME_REACT_NATIVE
```

### <img src="https://cdn.svgporn.com/logos/tauri.svg" align=left height="24" alt="react" icon="react" /> [Tauri](https://tauri.app/) Environment

#### Install [Xcode](https://developer.apple.com/xcode) and [Android Studio](https://developer.android.com/studio)

> [!NOTE]
> Use App Store to install **Xcode**

```sh
brew install android-studio
```

#### Set up Android Studio for Tauri Development

Use the SDK Manager in Android Studio to install the following SDK Tools:

- Android SDK Platform
- Android SDK Platform-Tools
- Android SDK Build-Tools
- Android SDK Command-line Tools
- NDK (Side by side)

> [!IMPORTANT]
> Add to `~/.config/fish/config.fish`

```fish
set -x JAVA_HOME_TAURI "/Applications/Android Studio.app/Contents/jbr/Contents/Home"
set -x ANDROID_HOME "$HOME/Library/Android/sdk"
set -x NDK_HOME "$ANDROID_HOME/ndk/(ls -1 $ANDROID_HOME/ndk)"
```

> [!WARNING]
> Verify the path of `ANDROID_HOME` is correct

#### Set `JAVA_HOME` environment variable for Tauri

```fish
set -x JAVA_HOME $JAVA_HOME_TAURI
```

#### Add Android and iOS targets

```sh
# Android
rustup target add aarch64-linux-android armv7-linux-androideabi i686-linux-android x86_64-linux-android
# iOS
rustup target add aarch64-apple-ios x86_64-apple-ios aarch64-apple-ios-sim
```

## Tools configs

### <img src="https://cdn.svgporn.com/logos/visual-studio-code.svg" align=left height="24" alt="visual-studio-code" /> Visual Studio Code (`settings.json`)

<details>

```jsonc
{
  "workbench.colorTheme": "Default Dark Modern",
  "workbench.iconTheme": "catppuccin-mocha",
  "workbench.productIconTheme": "icons-carbon",
  "terminal.integrated.fontFamily": "'Maple Mono NF CN', Menlo, monospace",
  "terminal.integrated.defaultProfile.osx": "fish",
  "terminal.external.osxExec": "Ghostty.app",
  "editor.fontFamily": "'Jasper Iosevka', 'Maple Mono NF CN', Menlo, monospace",
  "editor.fontLigatures": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnPaste": true,
  "editor.formatOnSave": true,
  "editor.linkedEditing": true,
  "editor.quickSuggestions": {
    "comments": "on",
    "strings": "on"
  },
  "editor.tabCompletion": "on",
  "editor.tabSize": 2,
  "files.associations": {
    "*.css": "tailwindcss"
  },
  // "javascript.inlayHints.functionLikeReturnTypes.enabled": true,
  // "typescript.inlayHints.functionLikeReturnTypes.enabled": true,
  // "javascript.inlayHints.parameterNames.enabled": "all",
  // "typescript.inlayHints.parameterNames.enabled": "all",
  // "javascript.inlayHints.parameterTypes.enabled": true,
  // "typescript.inlayHints.parameterTypes.enabled": true,
  "javascript.preferences.importModuleSpecifier": "non-relative",
  "typescript.preferences.importModuleSpecifier": "non-relative",
  "typescript.preferences.preferTypeOnlyAutoImports": true,
  "database-client.autoSync": true,
  "totalTypeScript.hideBasicTips": true,
  "telemetry.telemetryLevel": "error",
  "database-client.telemetry.usesOnlineServices": false,
  "gitlens.telemetry.enabled": false,
  "postman.telemetry.enabled": false,
  "totalTypeScript.hideAllTips": true,
  "github.copilot.chat.codesearch.enabled": true,
  "github.copilot.chat.completionContext.typescript.mode": "on",
  "github.copilot.chat.editor.temporalContext.enabled": true,
  "github.copilot.chat.edits.temporalContext.enabled": true,
  "github.copilot.chat.generateTests.codeLens": true,
  "github.copilot.chat.languageContext.typescript.enabled": true,
  "github.copilot.chat.agent.thinkingTool": true,
  "github.copilot.chat.languageContext.fix.typescript.enabled": true,
  "github.copilot.chat.languageContext.inline.typescript.enabled": true,
  "github.copilot.nextEditSuggestions.enabled": true,
  "chat.agent.enabled": true,
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": false,
    "scminput": false
  }
}
```

</details>

### Ghostty (`config`)

<details>

```txt
font-family = Maple Mono NF CN
font-size = 12
theme = Dark Pastel
minimum-contrast = 3
cursor-style-blink = false
background-opacity = 0.9
background-blur-radius = 3
command = /opt/homebrew/bin/fish
window-padding-x = 12
window-padding-y = 6
window-inherit-working-directory = true
window-colorspace = display-p3
shell-integration-features = no-cursor
bold-is-bright = true
```

</details>

## Project configs

### <img src="https://cdn.svgporn.com/logos/prettier.svg" align=left height="24" alt="prettier" /> Prettier (`prettier.config.js`)

<details>

```js
/** @type {import("prettier").Config} */
const prettierConfig = {
  // tailwindFunctions: ["cn", "cva"],
  // plugins: ["prettier-plugin-tailwindcss"],
  trailingComma: "es5",
  tabWidth: 2,
  semi: true,
  singleQuote: false,
  useTabs: true,
  bracketSpacing: true,
  printWidth: 80,
};

export default prettierConfig;
```

</details>

### <img src="https://cdn.svgporn.com/logos/eslint.svg" align=left height="24" alt="eslint" /> ESLint (`eslint.config.js`)

<details>

```js
/* @ts-check */

import { FlatCompat } from "@eslint/eslintrc";
import eslint from "@eslint/js";
import simpleImportSort from "eslint-plugin-simple-import-sort";
import eslintPluginUnicorn from "eslint-plugin-unicorn";
import globals from "globals";
import tseslint from "typescript-eslint";

/* utility to translate legacy eslintrc-style configs into flat configs */
const compat = new FlatCompat({ baseDirectory: import.meta.dirname });

const eslintConfig = tseslint.config(
  eslint.configs.recommended,
  tseslint.configs.strictTypeChecked,
  tseslint.configs.stylisticTypeChecked,
  eslintPluginUnicorn.configs.recommended,
  {
    plugins: { "simple-import-sort": simpleImportSort },
    rules: {
      "simple-import-sort/imports": "error",
      "simple-import-sort/exports": "error",
      "@typescript-eslint/consistent-type-imports": "error",
      "@typescript-eslint/consistent-type-exports": "error",
      "@typescript-eslint/consistent-type-definitions": ["error", "type"],
      "unicorn/better-regex": "warn",
    },
    languageOptions: {
      parserOptions: {
        projectService: true,
        tsconfigRootDir: import.meta.dirname,
      },
      globals: { ...globals.browser, ...globals.node },
    },
  }
);

export default eslintConfig;
```

</details>

<!-- markdownlint-disable MD033 -->

# MY CONFIG SHIT

Collection of settings and instructions to set up a new **macOS** machine

## Setting up

### <img src="https://cdn.svgporn.com/logos/homebrew.svg" align=left height="24" alt="homebrew" /> Set up [Homebrew](https://brew.sh) as package manager

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### <img src="https://cdn.simpleicons.org/fishshell" align=left height="24" alt="fish-shell" /> Install [Tabby](https://tabby.sh) and [Fish](https://fishshell.com), and download JetBrainsMono Nerd Font and SF Mono

```sh
brew install tabby fish font-jetbrains-mono-nerd-font font-sf-mono
```

### Set up [Fisher](https://github.com/jorgebucaran/fisher) as plugin manager for Fish

```sh
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

### Install [Tide](https://github.com/IlanCosman/tide) as shell prompt with [Fisher](https://github.com/jorgebucaran/fisher), then set up

```sh
fisher install IlanCosman/tide@v6
```

```fish
set --universal tide_node_icon "󰎙"
set --universal tide_cmd_duration_threshold 0
```

## Tools configs

### <img src="https://cdn.svgporn.com/logos/nodejs-icon.svg" align=left height="24" alt="node-js" /> [Node](https://nodejs.org) Environment

#### Install [nvm.fish](https://github.com/jorgebucaran/nvm.fish) with [Fisher](https://github.com/jorgebucaran/fisher)

```sh
fisher install jorgebucaran/nvm.fish
```

#### Install Node versions

```sh
# Current
nvm install latest
# LTS
nvm install lts/jod
```

#### Set a default version

```fish
set --universal nvm_default_version latest
```

### <img src="https://cdn.svgporn.com/logos/python.svg" align=left height="24" alt="python" /> [Python](https://www.python.org) Environment

#### Install [pyenv](https://github.com/pyenv/pyenv)

```sh
brew install pyenv
```

#### Install Python versions

```sh
# Current
pyenv install 3.13.0
```

#### Set version

```sh
# Global
pyenv global 3.13.0
# Project Specific
pyenv local 3.13.0
```

### <img src="https://cdn.svgporn.com/logos/ruby.svg" align=left height="24" alt="python" /> [Ruby](https://www.ruby-lang.org) Environment

#### Install [rbenv](https://github.com/rbenv/rbenv)

```sh
brew install rbenv
```

#### Install Ruby versions

```sh
# Current
rbrnv install 3.3.6
```

#### Set version

```sh
# Global
rbenv global 3.3.6
# Project Specific
rbenv local 3.3.6
```

### <img src="https://cdn.svgporn.com/logos/visual-studio-code.svg" align=left height="24" alt="visual-studio-code" /> Visual Studio Code (`settings.json`)

<details>

```json
{
  "workbench.colorTheme": "Default Dark Modern",
  "workbench.iconTheme": "catppuccin-mocha",
  "workbench.productIconTheme": "icons-carbon",
  "terminal.integrated.fontFamily": "'SF Mono', 'JetBrainsMono Nerd Font', Menlo, monospace",
  "terminal.integrated.defaultProfile.osx": "fish",
  "terminal.external.osxExec": "Tabby.app",
  "editor.fontFamily": "'Jasper Iosevka', 'SF Mono', 'JetBrainsMono Nerd Font', Menlo, monospace",
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
  "javascript.experimental.updateImportsOnPaste": true,
  "typescript.experimental.updateImportsOnPaste": true,
  "typescript.preferences.preferTypeOnlyAutoImports": true,
  "telemetry.telemetryLevel": "error",
  "database-client.telemetry.usesOnlineServices": false,
  "gitlens.telemetry.enabled": false,
  "postman.telemetry.enabled": false,
  "totalTypeScript.hideBasicTips": true
}
```

</details>

### Tabby (`config.yaml`)

<details>

```yaml
hotkeys:
  copy-current-path: []
  ctrl-c:
    - Ctrl-C
  copy:
    - ⌘-C
  paste:
    - ⌘-V
  clear:
    - ⌘-K
  select-all:
    - ⌘-A
  zoom-in:
    - ⌘-=
    - ⌘-Shift-=
  zoom-out:
    - ⌘--
    - ⌘-Shift--
  reset-zoom:
    - ⌘-0
  home:
    - ⌘-Left
    - Home
  end:
    - ⌘-Right
    - End
  previous-word:
    - ⌥-Left
  next-word:
    - ⌥-Right
  delete-previous-word:
    - ⌥-Backspace
  delete-line:
    - ⌘-Backspace
  delete-next-word:
    - ⌥-Delete
  search:
    - ⌘-F
  pane-focus-all:
    - ⌘-Shift-I
  focus-all-tabs:
    - ⌘-⌥-Shift-I
  scroll-to-top:
    - Shift-PageUp
  scroll-up:
    - ⌥-PageUp
  scroll-down:
    - ⌥-PageDown
  scroll-to-bottom:
    - Shift-PageDown
  restart-telnet-session: []
  restart-ssh-session: []
  launch-winscp: []
  settings-tab: {}
  settings:
    - ⌘-,
  serial:
    - Alt-K
  restart-serial-session: []
  new-tab:
    - ⌘-T
  toggle-window:
    - Ctrl-Space
  new-window:
    - ⌘-N
  profile: {}
  profile-selectors: {}
  toggle-fullscreen:
    - Ctrl+⌘+F
  close-tab:
    - ⌘-W
  reopen-tab:
    - ⌘-Shift-T
  toggle-last-tab: []
  rename-tab:
    - ⌘-R
  next-tab:
    - Ctrl-Tab
  previous-tab:
    - Ctrl-Shift-Tab
  move-tab-left:
    - ⌘-Shift-Left
  move-tab-right:
    - ⌘-Shift-Right
  rearrange-panes:
    - Ctrl-Shift
  tab-1:
    - ⌘-1
  tab-2:
    - ⌘-2
  tab-3:
    - ⌘-3
  tab-4:
    - ⌘-4
  tab-5:
    - ⌘-5
  tab-6:
    - ⌘-6
  tab-7:
    - ⌘-7
  tab-8:
    - ⌘-8
  tab-9:
    - ⌘-9
  tab-10: []
  duplicate-tab: []
  restart-tab: []
  reconnect-tab: []
  disconnect-tab: []
  explode-tab:
    - ⌘-Shift-.
  combine-tabs:
    - ⌘-Shift-,
  tab-11: []
  tab-12: []
  tab-13: []
  tab-14: []
  tab-15: []
  tab-16: []
  tab-17: []
  tab-18: []
  tab-19: []
  tab-20: []
  split-right:
    - ⌘-Shift-D
  split-bottom:
    - ⌘-D
  split-left: []
  split-top: []
  pane-nav-right:
    - ⌘-⌥-Right
  pane-nav-down:
    - ⌘-⌥-Down
  pane-nav-up:
    - ⌘-⌥-Up
  pane-nav-left:
    - ⌘-⌥-Left
  pane-nav-previous:
    - ⌘-⌥-[
  pane-nav-next:
    - ⌘-⌥-]
  pane-nav-1: []
  pane-nav-2: []
  pane-nav-3: []
  pane-nav-4: []
  pane-nav-5: []
  pane-nav-6: []
  pane-nav-7: []
  pane-nav-8: []
  pane-nav-9: []
  pane-maximize:
    - ⌘-⌥-Enter
  close-pane:
    - ⌘-Shift-W
  pane-increase-vertical: []
  pane-decrease-vertical: []
  pane-increase-horizontal: []
  pane-decrease-horizontal: []
  profile-selector:
    - ⌘-E
  switch-profile:
    - ⌘-Shift-E
  command-selector:
    - ⌘-Shift-P
terminal:
  frontend: xterm-webgl
  fontSize: 12
  fontWeight: 400
  fontWeightBold: 700
  fallbackFont: JetBrainsMono Nerd Font
  linePadding: 0
  bell: "off"
  bracketedPaste: true
  background: theme
  ligatures: true
  cursor: block
  cursorBlink: false
  hideTabIndex: false
  showTabProfileIcon: false
  hideCloseButton: false
  hideTabOptionsButton: false
  rightClick: menu
  pasteOnMiddleClick: true
  copyOnSelect: false
  copyAsHTML: true
  scrollOnInput: true
  altIsMeta: false
  wordSeparator: ' ()[]{}''"'
  colorScheme:
    name: Tabby Default
    foreground: "#cacaca"
    background: "#171717"
    cursor: "#bbbbbb"
    colors:
      - "#000000"
      - "#ff615a"
      - "#b1e969"
      - "#ebd99c"
      - "#5da9f6"
      - "#e86aff"
      - "#82fff7"
      - "#dedacf"
      - "#313131"
      - "#f58c80"
      - "#ddf88f"
      - "#eee5b2"
      - "#a5c7ff"
      - "#ddaaff"
      - "#b7fff9"
      - "#ffffff"
  lightColorScheme:
    name: Tabby Default Light
    foreground: "#4d4d4c"
    background: "#ffffff"
    cursor: "#4d4d4c"
    colors:
      - "#000000"
      - "#c82829"
      - "#718c00"
      - "#eab700"
      - "#4271ae"
      - "#8959a8"
      - "#3e999f"
      - "#ffffff"
      - "#000000"
      - "#c82829"
      - "#718c00"
      - "#eab700"
      - "#4271ae"
      - "#8959a8"
      - "#3e999f"
      - "#ffffff"
  customColorSchemes: []
  warnOnMultilinePaste: true
  searchRegexAlwaysEnabled: false
  searchOptions:
    regex: false
    wholeWord: false
    caseSensitive: false
  detectProgress: true
  scrollbackLines: 25000
  drawBoldTextInBrightColors: true
  sixel: true
  minimumContrastRatio: 4
  trimWhitespaceOnPaste: true
  font: SF Mono
  autoOpen: true
  useConPTY: true
  environment: {}
  setComSpec: false
  profile: local:opthomebrewbinfish
  showBuiltinProfiles: true
  showRecentProfiles: 3
  paneResizeStep: 0.1
  focusFollowsMouse: false
  identification: null
ssh:
  warnOnClose: false
  winSCPPath: null
  agentType: auto
  agentPath: null
  x11Display: null
  knownHosts: []
  verifyHostKeys: true
configSync:
  configID: null
  auto: false
  parts:
    hotkeys: true
    appearance: true
    vault: true
clickableLinks:
  modifier: null
accessibility:
  animations: true
appearance:
  dock: "off"
  dockScreen: current
  dockFill: 0.5
  dockSpace: 1
  dockHideOnBlur: false
  dockAlwaysOnTop: true
  flexTabs: false
  tabsLocation: top
  tabsInFullscreen: false
  cycleTabs: true
  theme: Follow the color scheme
  frame: thin
  css: "/* * { color: blue !important; } */"
  vibrancyType: blur
  lastTabClosesWindow: false
  spaciness: 1
  colorSchemeMode: dark
  vibrancy: true
  opacity: 0.9
profiles: []
groups: []
profileDefaults:
  ssh:
    disableDynamicTitle: true
recoverTabs: true
enableAnalytics: false
enableWelcomeTab: false
electronFlags:
  - - force_discrete_gpu
    - "0"
enableAutomaticUpdates: true
hideTray: false
version: 7
vault: null
encrypted: false
enableExperimentalFeatures: false
commandBlacklist: []
providerBlacklist: []
profileBlacklist: []
hacks:
  disableGPU: false
  disableVibrancyWhileDragging: false
  enableFluentBackground: false
language: null
defaultQuickConnectProvider: ssh
pluginBlacklist: []
```

</details>

## Project configs

### <img src="https://cdn.simpleicons.org/prettier" align=left height="24" alt="prettier" /> Prettier (`prettier.config.js`)

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

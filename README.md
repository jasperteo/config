# MY CONFIG SHIT

Collection of settings and instructions to set up a new **macOS** machine

## Setting up

### Set up [macOS](https://macos-defaults.com/)

```sh
defaults write com.apple.dock "orientation" -string "left"
defaults write com.apple.dock "tilesize" -int "40"
defaults write com.apple.dock "show-recents" -bool "false"
defaults write NSGlobalDomain "AppleShowAllExtensions" -bool "true"
defaults write com.apple.finder "AppleShowAllFiles" -bool "true"
defaults write com.apple.finder "ShowPathbar" -bool "true"
defaults write com.apple.finder "FXRemoveOldTrashItems" -bool "true"
defaults write com.apple.universalaccess "showWindowTitlebarIcons" -bool "true"
defaults write com.apple.finder "ShowStatusBar" -bool "true"
defaults write com.apple.menuextra.clock "FlashDateSeparators" -bool "true"
defaults write com.apple.menuextra.clock "DateFormat" -string "\"EEE d MMM HH:mm:ss\""
killall Dock && killall Finder
```

### <img src="https://svgl.app/library/homebrew.svg" align=left height="32" alt="homebrew" /> Set up [Homebrew](https://brew.sh) as package manager

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Install [Fish](https://fishshell.com) and [Ghostty](https://ghostty.org/), then download SF Mono

```bash
brew install fish ghostty font-sf-mono
```

### Set up [Fisher](https://github.com/jorgebucaran/fisher) as plugin manager for Fish

```bash
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

### Install [Tide](https://github.com/IlanCosman/tide) as shell prompt with [Fisher](https://github.com/jorgebucaran/fisher)

```bash
fisher install IlanCosman/tide
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

### Install [Catppuccin](https://github.com/catppuccin/fish) as theme

```bash
fisher install catppuccin/fish
```

#### Set theme

```fish
fish_config theme choose catppuccin-mocha
```

### <img src="https://svgl.app/library/vscode.svg" align=left height="32" alt="visual-studio-code" /> Install [Visual Studio Code](https://code.visualstudio.com)

```bash
brew install visual-studio-code
```

### <img src="https://svgl.app/library/git.svg" align=left height="32" alt="git" /> Install [Git](https://git-scm.com)

```bash
brew install git
```

#### Configure git

```bash
git config --global user.name "Jasper 張"
git config --global user.email "jaspertzj@outlook.sg"
git config --global core.editor "code --wait"
git config --global rebase.ff only
```

### Install other software

```bash
brew install 1password microsoft-edge@dev firefox@developer-edition raycast macs-fan-control rectangle keka cloudflare-warp iina fastfetch btop
brew install kekaexternalhelper
```

#### <img src="https://svgl.app/library/docker.svg" align=left height="32" alt="docker" /> [OrbStack](https://orbstack.dev) (Docker Desktop Alternative)

```bash
brew install orbstack
```

## Environment configs

### <img src="https://svgl.app/library/pnpm_dark.svg" align=left height="32" alt="pnpm" /> [pnpm](https://pnpm.io/) Environment

```bash
curl -fsSL https://get.pnpm.io/install.sh | sh -
```

#### <img src="https://svgl.app/library/nodejs.svg" align=left height="32" alt="node" /> Install [Node](https://nodejs.org/) versions

```bash
# Current
pnpm runtime set node latest -g
# LTS
pnpm runtime set node lts -g
```

#### <img src="https://svgl.app/library/deno_dark.svg" align=left height="32" alt="deno" /> Install [Deno](https://deno.com/)

```bash
pnpm runtime set deno latest -g
```

#### <img src="https://svgl.app/library/bun.svg" align=left height="32" alt="bun" /> Install [Bun](https://bun.sh/)

```bash
pnpm runtime set bun latest -g
```

## Tools configs

### <img src="https://svgl.app/library/ghostty.svg" align=left height="32" alt="ghostty" /> [Ghostty](https://ghostty.org/) (`config`)

<details>

```txt
font-family = Maple Mono NF CN
font-size = 12
theme = IBM 5153 CGA (Black)
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
macos-icon = xray
```

</details>

### [Fish](https://fishshell.com) (`config.fish`)

<details>

```fish
# pnpm
set -gx PNPM_HOME $HOME/Library/pnpm
fish_add_path -g $PNPM_HOME

if status is-interactive
    # Mole shell completion
    if type -q mole
        mole completion fish | source
    end
end
```

</details>
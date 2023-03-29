# Setting Up a New Mac

## [Install iTerm2](https://iterm2.com/)

Change `Preferences > Profiles > Default Profile > Colors > Color Presets...` to be **Solarized Dark**

Install Apple Developer Tools

If not prompted by installation of iTerm2, run `xcode-select --install`.

[Install oh-my-zsh](https://ohmyz.sh/#install)

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

[Install zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh)

[Install Homebrew](https://brew.sh)

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Don't forget to run:
```
(echo; echo 'eval "$(/usr/local/bin/brew shellenv)"') >> /Users/jford/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```
_Note: the above command may differ depending on which architecture you're on (e.g. Intel, Apple Silicon).
Refer to the Homebrew installation "Next steps:" output for the actual command._

[Install p10k](https://github.com/romkatv/powerlevel10k#homebrew)
```
brew install romkatv/powerlevel10k/powerlevel10k
```

Install p10k fonts
```
p10k configure
```

[Setup Passwordless Sudo](https://apple.stackexchange.com/questions/257813/enable-sudo-without-a-password-on-macos)

```
sudo visudo
```

`%admin ALL=(ALL) ALL`

⬇️

`%admin ALL=(ALL) NOPASSWD: ALL`

[Install Jump](https://github.com/gsamokovarov/jump)
```
brew install jump
```

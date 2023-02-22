# Setting Up a New Mac

## [iTerm2](https://iterm2.com/)

Install Apple Developer Tools

[Install oh-my-zsh](https://ohmyz.sh/#install)

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

[Install Homebrew](https://brew.sh)

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Don't forget to run:
```
(echo; echo 'eval "$(/usr/local/bin/brew shellenv)"') >> /Users/jford/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```

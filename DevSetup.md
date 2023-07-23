# New MBP Setup

## OS & System Software

- System -> Trackpad
    - Point & Click -> Set “Look up & data detectors” to “Tap with three fingers”
    - Point & Click -> Check “Tap to click”
    - More Gestures -> Swipe between pages -> change to “Swipe with three fingers”
- System -> Keyboard
    - Check Use F1, F2. etc keys as standard function keys
- Terminal -> Preferences…
    - Profiles -> Basic -> Window -> set window size to 120x32
    - Shell -> When the shell exits -> Close the window
- Install `homebrew`
- Install & configurate `on-my-zsh`
  - Add `export PATH=/opt/homebrew/bin:$PATH` to `.zshrc`

## Node.js

```
brew install node
npm install pm2@latest -g
```

## Python

- python3: `brew install python3`
- [pipx](https://pypa.github.io/pipx/) - install & run python apps in isolated envs: `brew install pipx`

## AWS CLI

- awscli: `brew install awscli`
- [aws-export-credentials](https://github.com/benkehoe/aws-export-credentials) - export to credentials file when using AWS SSO
    - install: `pipx install aws-export-credentials`
    - configure sso-session and profiles first: `aws configure sso`
    - auth using sso when needed: `aws sso login --profile prod`
    - then export to credentials file: `aws-export-credentials --profile prod -c prod`

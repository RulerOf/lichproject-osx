# Lichproject on High Sierra

This repo is intended to act as a convenient package and easy-to-use installation guide for the lichproject proxy used with several play.net games.

Follow the instructions below to get the software working on your computer.

## Requirements

- [Homebrew](https://brew.sh/)
- Wine. I suggest following [this guide](https://www.davidbaumgold.com/tutorials/wine-mac/#part-1:-install-homebrew), parts 1-3.

## Usage

### Install Lich

Clone this repo to your machine and then change to that directory:

```bash
git clone https://github.com/RulerOf/lichproject-osx.git ~/lich
cd ~/lich
```

Update Homebrew, then install `rbenv` and the supporting tools we need:

```bash
brew update
brew install rbenv ruby-build rbenv-gemset
```

Install Cairo and xQuartz:

```bash
brew install --with-x11 cairo
brew tap Caskroom/cask
brew cask install xquartz
```

Install and pin the version of gtk+ that is required by Lich:

```bash
brew install https://raw.githubusercontent.com/Homebrew/homebrew/bb3fe5f2de87f76bc0a3f3480635c8fd0d68cec3/Library/Formula/gtk+.rb
brew pin gtk+
```

Initialize `rbenv` and integrate it with your shell:

```bash
eval "$(rbenv init -)"
if [[ "$SHELL" = *"bash"* ]]; then
  shellInitFile=~/.bash_profile
elif [[ "$SHELL" = *"zsh"* ]]; then
  shellInitFile=~/.zshrc
fi
printf '# Initialize rbenv\neval "$(rbenv init -)"\n' >> $shellInitFile
```

Install the version of Ruby required by Lich:

```bash
rbenv install -s
```

Install bundler, and then install the required gems:

```bash
gem install bundler
rbenv rehash
bundle install
```

### Install Simutronics Launcher

Download the executable:

```bash
curl -OL http://www.play.net/software/lnchInst.exe
```

Run it with wine:

```bash
wine lnchInst.exe
```

Click through that installation.

### Running Lich

Now run lich:

```bash
ruby lich.rbw
```

Enter your username and password into the lich settings, connect, choose your launcher, and run the game. Your system will download and run either the StormFront or Wizard Front End, and it will run under wine.

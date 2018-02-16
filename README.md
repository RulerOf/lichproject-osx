# Lichproject on High Sierra

## Overview

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
brew install rbenv ruby-build rbenv-gemset rbenv-bundler
```

Initialize `rbenv` and integrate it with your shell:
 - Note: follow the instructions printed by `rbenv init -` if you use a different shell

```bash
rbenv init -
printf '# Initialize rbenv\neval "$(rbenv init -)"\n' >> ~/.bash_profile
```

Install the version of Ruby required by Lich:

```bash
rbenv install -v 2.2.5
```

Create a Gemset that we can use with Lich:

```bash
rbenv gemset init lichproject
```

Install bundler, enable `rbenv-bundler`, and then install the required gems:

```bash
gem install bundler
rbenv bundler on
bundler install
```

### Install Simutronics Launcher

Download the executable:

```bash
wget http://www.play.net/software/lnchInst.exe
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

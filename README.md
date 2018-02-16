
Update Homebrew and install `rbenv` and the supporting tools we need:

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

Now run lich:

```bash
ruby lich.rbw
```

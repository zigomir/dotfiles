Forked from my [ZSH dotfiles](https://github.com/caarlos0/dotfiles), those are
my Fish Shell config files, together with editor, macOS configs and other
goodies.

The main reasons for the fork are:

- a lot of things I have out of the box on Fish needed plugins on zsh
- Fish autocompletion is awesome
- Fish syntax is easier to use
- Fish is more modern.

This is an attempt to make the same things I had on my ZSH dotfiles on Fish.
For the user, it should look pretty much the same, although under the hood
there are a lot of changes.

Config files are still topical, and even though aliases are not a thing on Fish,
files are named like that still (and hold both functions and abbreviations).

The auto-update feature was removed, as it was hacky on ZSH and I didn't want to
do it. Instead, now the bootstrap script is better and can be run multiple times
without any issues, so, to update, `git pull` and run the `bootstrap.fish`
script.

## Installation

### Dependencies

First, make sure you have all those things installed:

- `git`: to clone the repo
- `curl`: to download some stuff
- `tar`: to extract downloaded stuff
- `fish`: the shell
- `sudo`: some configs may need that

### Install

Then, run these steps:

```console
$ git clone https://github.com/caarlos0/dotfiles.fish.git ~/.dotfiles
$ cd ~/.dotfiles
$ ./script/bootstrap.fish
```

> All changed files will be backed up with a `.backup` suffix.

#### Update

To update, you just need to `git pull` and run the bootstrap script again:

```console
$ cd ~/.dotfiles
$ git pull origin master
$ ./script/bootstrap.fish
```

## Revert

Reverting is not totally automated, but it pretty much consists in removing
the fish config and dotfiles folder, as well as moving back some config files.

**Remove the folders:**

```console
$ rm -rf ~/.dotfiles ~/.config/fish
```

**Some config files were changed, you can find them using `fd`:**

```console
$ fd -e backup -e local -H -E Library -d 3 .
```

And then manually inspect/revert them.

## macOS defaults

You use it by running:

```console
~/.dotfiles/macos/set-defaults.sh
```

And logging out and in again or restart.

# Pipas' Linux Config Guide

## Introduction

The purpose of this repository is to serve as a **personal** checklist to install and configure linux to my liking as fast possible.

Do keep in mind that I'm not a Linux expert or claim to be one, what I'm most looking for in a distro is ease of use and maintainability so it might not be what you're looking for.

I plan to maintain this repository for myself and things will be updated over time as I change my personal config, learn and discover new things.

### Community Update

After initially writing this guide I've received suggestions and feedback that I would like to incorporate into it. To achieve this without deviating too much from the main goal of the project (to serve as a personal checklist) these suggestions will be marked with an icon (👥) and may not be used by me, personally.

If you'd also like to contribute to this repository in any way or suggest something feel free to do so by submitting an [issue](https://github.com/Pipas/LinuxConfig/issues).

## Screenshots

![Screenshot1](screenshots/screenshot1.png)
![Screenshot2](screenshots/screenshot2.png)

## Table of Contents
  - [Distro](#distro)
  - [Pre-requisites](#pre-requisites)
  - [Look](#look)
  - [Extensions](#extensions)
  - [Touchpad Gestures](#touchpad-gestures)
  - [Albert](#albert)
  - [Terminal](#terminal)
  - [Development](#development)
  - [Other Software](#other-software)
  - [Snap Software](#snap-software)
  - [Contributors](#contributors)

## Distro

Following the theme of ease of use [Ubuntu 19.04](https://ubuntu.com/download/desktop) is my distro of choice as I found it to be the most hassle free distribution of Linux. It's well support by most mainstream apps (like Spotify and Discord) and the community support is great for those who want a nice experience without needing to delve to deep into the system. I have tried Fedora, Manjaro and Arch in the past but keep coming back to Ubuntu for these reasons. Also [PPAs](https://en.wikipedia.org/wiki/Ubuntu#Package_Archives).

## Pre-requisites

To start, clone this repository in your home directory (I clone it to a dot folder so it doesn't show up in file managers)

```shell
git clone https://github.com/Pipas/LinuxConfig .dotfiles
```

## Look

I use Gnome as my desktop environment, it comes built in with new versions of Ubuntu and I found it to work best for me.

A great piece of software to aid your customization of gnome is `Gnome Tweak Tool`

```shell
sudo apt install gnome-tweak-tool
```

Another helper to faster install themes from the [gnome-look.org](gnome-look.org) is [`OCS-url`](https://www.pling.com/p/1136805/).

Here are the themes that I use.

### Gnome and Shell theme 
 - [Macterial](https://www.gnome-look.org/p/1248255/) by MYHTIO

### Icon theme
- [Paper](https://snwh.org/paper) by Sam Hewitt

### Cursor theme
- [Bibata](https://www.gnome-look.org/p/1197198/) by KaizIqbal

### Fonts

The fonts I use for my distro can be found in a fonts folder in this repo. To use them copy them to .fonts
```shell
mkdir ~/.fonts
cp ~/.dotfiles/fonts/* ~/.fonts
```

To set them use the Tweak Tool, here are the values I use:

- Interface Text - **SFNS Display Bold** 12
- Document Text - **SFNS Display Regular** 12
- Monospace Text - **SF Mono Regular** 13
- Legacy Window Titles - **SFNS Display Bold** 12

## Extensions

There are several Gnome extensions that make the experience much better and tweak the system to your liking. There are many to choose from at [extensions.gnome.org](https://extensions.gnome.org/) and here are some of the ones I use.

- #### [User Themes](https://extensions.gnome.org/extension/19/user-themes/) - **needed to change the default shell theme**, as stated in all the comments should be enabled by default.

- #### [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/) - changes the gnome bar to a dock, highly customizable.

- #### [Argos](https://extensions.gnome.org/extension/1176/argos/) - loads Gnome extensions, used to display spotify current track on top bar.

- #### [OpenWeather](https://extensions.gnome.org/extension/750/openweather/) - weather indicator on your top bar, useful to have at times, highly customizable.

- #### [system-monitor](https://extensions.gnome.org/extension/120/system-monitor/) - displays system information in the top bar such as cpu, mem and network.~~

- #### [Remove App Menu](https://extensions.gnome.org/extension/591/remove-app-menu/) - Removes app menu from top bar to reduce clutter.

- #### [Hide Activities Button](https://extensions.gnome.org/extension/744/hide-activities-button/) - hides the activities button.

- #### [GS Connect](https://extensions.gnome.org/extension/1319/gsconnect/) - connects with KDE Connect. [👥](https://github.com/Pipas/LinuxConfig/pull/3)

### Spotify Display
On the folder argos you can find a script that adds your currently playing song to the Gnome top bar. To install it after installing the [Argos](https://extensions.gnome.org/extension/1176/argos/) extension described above, copy the contents of this folder to the argos config location

```shell
cp ~/.dotfiles/argos/mpris.6l.1s.sh ~/.config/argos/mpris.6l.1s.sh
```
then make the file executable

```shell
chmod +x ~/.config/argos/mpris.6l.1s.sh
```

This extension was created by giedriusStan and tweaked by me, the original repository can be found [here](https://github.com/giedriusStan/argos-mpris).


## Touchpad Gestures

If you're using Linux in a laptop with a modern touchpad enabling gestures is a no brainer to increase productivity, I have achieved this with a program called [fusuma](https://github.com/iberianpig/fusuma) pointed out in [this](https://askubuntu.com/a/1044184) response by Rachit Kinger on an askubuntu question, I am pasting the answer here as I might change it in the future if need be.

First of all check if your current user is part of the input group. You can do that by

```shell
sudo gpasswd -a $USER input  
```

Then log out and log back in. Now install xdotool and libinput-tools.

```shell
sudo apt-get install libinput-tools  

sudo apt-get install xdotool  
```

If you haven't installed Ruby you can do that now:

```shell
sudo apt install ruby  
```

Now install fusuma

```shell
sudo gem install fusuma  
```

My personal gestures file is in this repository in the folder called fusuma, to use it create a symlink to this folder at `~/.config`

```shell
ln -s ~/.dotfiles/fusuma ~/.config/fusuma
```

Test if everything is working before adding the fusuma command to your startup applications.
```shell
sudo fusuma
```

In Ubuntu you can do it by searching for the `Startup Applications` and adding `fusuma` as a command.

---
Alternatively you can use [libinput-gestures](https://github.com/bulletmark/libinput-gestures) [👥](https://github.com/Pipas/LinuxConfig/pull/3)


## Albert

[Albert](https://albertlauncher.github.io/) is a desktop launcher for linux, it's simple, fast and it helps you get to what you want faster. I use Albert quite a lot and I have it bound to the *windows* (super) key on my keyboard.

To do this we first start with installing Albert, instructions on how to do it can be found [here](https://software.opensuse.org/download.html?project=home:manuelschneid3r&package=albert).

After albert is installed, open it and bind the Hotkey combination to `ctrl + Space`.

Now we can bind the super key to that combination so when pressed it'll toggle Albert, first unbind the key in gnome
```shell
gsettings set org.gnome.mutter overlay-key ""
```

and then we'll use xcape to bind it.

First install xcape
```shell
sudo apt install xcape
```

Then you can add both
```shell
xcape -e 'Super_L=Control_L|space'
```
and
```shell
albert
```
to your `Startup Applications` so they both run when you boot the system.

## Terminal

My shell of choice is ZSH with the [Spaceship prompt](https://github.com/denysdovhan/spaceship-prompt). The installation process for this is extremely easy since zplug handles most of it if you use my `.zshrc` file.

First we need to install zsh (we'll also install the powerline fonts needed for the prompt)
```shell
sudo apt install zsh
sudo apt install powerline fonts-powerline
```
I also had to install Google Noto Fonts `sudo apt install fonts-noto` so that the emojis could work properly.

Now change the default shell to zsh
```shell
chsh -s $(which zsh)
```
Install zplug
```shell
curl -sL --proto-redir -all,https https://raw.githubusercontent.com/zplug/installer/master/installer.zsh | zsh
```

Create a symlink to the `.zshrc` file
```shell
ln -s ~/.dotfiles/.zshrc ~/.zshrc
```

Finally logout to apply the changes.

When opening the terminal again you'll be prompted if you want to install missing plugins just press Y and wait. You'll get a pyenv error but I'll explain how to install pyenv in the next section.

___

or alternatively:

`npm install -g spaceship-prompt`

## Development

### pyenv

I use [pyenv](https://github.com/pyenv/pyenv) to manage python virtual environments and versions for all my python projects, it can easely be installed by using the [pyenv-installer](https://github.com/pyenv/pyenv-installer).
Check the [wiki](https://github.com/pyenv/pyenv/wiki) to install the necessary dependencies for installing python versions.
### nvm 
I use [nvm](https://github.com/nvm-sh/nvm) to manage npm environments and versions for all my npm projects, it can easely be installed by using `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash`. [👥](https://github.com/Pipas/LinuxConfig/pull/3)

### [docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04) and [docker-compose](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04) [👥](https://github.com/Pipas/LinuxConfig/pull/3)

### ssh keys
If you are like me and you forget to copy your ssh keys [every](https://help.github.com/en/articles/checking-for-existing-ssh-keys) ...[fucking](https://help.github.com/en/enterprise/2.16/user/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) ...[time](https://help.github.com/en/enterprise/2.15/user/articles/adding-a-new-ssh-key-to-your-github-account) follow the links to check/generate/add new ones. [👥](https://github.com/Pipas/LinuxConfig/pull/3)


## Other Software

- #### [TLP](https://linrunner.de/en/tlp/tlp.html) - Linux Advanced Power Management.
- #### [CherryTree](https://www.giuspen.com/cherrytree/) - A hierarchical note taking application, featuring rich text and syntax highlighting, storing data in a single xml or sqlite file. [👥](https://github.com/Pipas/LinuxConfig/pull/3)
- #### [KeeWeb](https://keeweb.info/) - Free cross-platform password manager compatible with KeePass. [👥](https://github.com/Pipas/LinuxConfig/pull/3)
- #### [Intellij](https://www.jetbrains.com/idea/) - Integrated development environment (IDE) for developing computer software. [👥](https://github.com/Pipas/LinuxConfig/pull/3)

## Snap Software [👥](https://github.com/Pipas/LinuxConfig/pull/3)
You can search thousands of snaps used by millions of people across 41 Linux distributions in the [snap](https://media1.tenor.com/images/e36fb32cfc3b63075adf0f1843fdc43a/tenor.gif?itemid=12502580) [store](https://snapcraft.io/store)
I like:
- [Slack](https://snapcraft.io/slack)
- [Discord](https://snapcraft.io/discord)
- [Sublime](https://snapcraft.io/sublime-text)
- [VSCode](https://snapcraft.io/code)
- [VLC](https://snapcraft.io/vlc)
- [Spotify](https://snapcraft.io/spotify) - 4k displays owners click [here](https://community.spotify.com/t5/Desktop-Linux/Spotify-Hi-DPI-Fix-for-Snap-install/td-p/4576328) or [here](https://www.amazon.com/s?k=magnifier&crid=3HJHDUKJU50N8&sprefix=Magnifier%2Caps%2C396&ref=nb_sb_ss_i_1_9)

## Contributors
A big thanks to everyone that helped by either suggesting or contributing to this guide, you can find them and their projects here:

- [Afonso Pinto](https://github.com/afonsobspinto)
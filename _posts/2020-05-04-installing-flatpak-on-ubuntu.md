---
layout: post
title:  "Installing Flatpak on Ubuntu 18.04"
categories: vim
date:   2020-05-04 16:00:00 +0700
permalink: flatpak-install-ubuntu/
---
Flatpak is a universal packaging for linux. It has an app center called [Flathub](https://flathub.org/home) in which you can install many softwares into your linux machine.

To be able to install any software from flathub, you need to install Flatpak first into your machine. Here's how to:

## Install Flatpak

To install the latest version of flatpak, add the flatpak ppa repository and then install it:

```
sudo add-apt-repository ppa:alexlarsson/flatpak 
sudo apt update 
sudo apt install flatpak
```

Now you should have flatpak installed in your system.

## Installing gnome-software-plugin-flatpak

When you install a new software from flathub, your new software will not automatically have a proper icon in ubuntu desktop launcher. To make this process automatic, you should install gnome plugin for flatpak.

```
sudo apt install gnome-software-plugin-flatpak
```

Now everytime you install a new software from flatpak repository, you should have a corresponding icon in gnome launcher automatically.

## Add a flatpak repository
The main repository for flatpak applications is [Flathub](https://flathub.org/home). You need to add the repository so you can search and install application that's published in that repository. Now add flathub into your flatpak repository:

```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

## Searching flatpak apps.
You can search the apps that you need in flathub, click Install and it should bring you to ubuntu software application just like when you install a `.deb` package. However it doesn't works for me, so the alternative way is to use the terminal.

To search for an application in flatpak repository, type this command:

```
flatpak search <your-query>

// for example
flatpak search planner
```

should give you the list of flatpak package containing the word of your query.

After you get the application that you want, you can install it by running:

```
flatpak install <Application ID>
```

For example in this case if I want to install Planner I will type:

```
flatpak install  com.github.alainm23.planner
```

Flatpak will ask you about several things like permission access and dependency installation, just type yes and you're good to go. Now you should have a flatpak apps installed in your machine and you should be access it through gnome launcher.

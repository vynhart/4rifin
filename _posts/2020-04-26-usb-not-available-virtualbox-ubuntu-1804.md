---
layout: post
title:  "Fix usb not available in Virtual box with host Ubuntu 18.04"
categories: linux
date:   2020-04-26 19:00:00 +0700
permalink: virtualbox-usb-not-available-ubuntu-1804/
---
If you encounter that your virtualbox doesn't detect any USB port of your host,
and you know that you already installed the Virtualbox extension pack,
try to add your username into vboxusers with this command:

```
sudo adduser $USER vboxusers
```

After that, logout and login back. It works for me I hope it works for you too.

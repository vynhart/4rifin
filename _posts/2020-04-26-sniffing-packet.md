---
layout: post
title:  "Sniffing packet"
categories: kali
date:   2020-04-26 20:00:00 +0700
permalink: sniffing-packet-with-wireless-card/
---
After you successfully set your wireless card into monitoring mode,
now you can start to sniffing packet that transferred into the air.

To do that, run airodump-ng followed the name of your wireless interface,
for example:

```
$ airodump-ng wlan0
```

now you should see airodump shows the available wireless host mac address and the station
(device that's connected to it) as well

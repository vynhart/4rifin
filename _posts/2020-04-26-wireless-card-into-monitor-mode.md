---
layout: post
title:  "Wireless card into monitor mode"
categories: kali
date:   2020-04-26 19:00:00 +0700
permalink: wireless-card-into-monitor-mode/
---
Check the name of your wireless card by running command:

```
$ iwconfig
```

That command will show you the list of wireless card thats available in your machine, in my case, it's wlan0.

Then, turn off the wireless card by running the following command, note that you might need to replace `wlan0` according
to the name of your wireless card

```
$ ifconfig wlan0 down
```

After that, it would be better to kill any process that might interfere when we're using monitor mode.

```
$ airmon-ng check kill
```

And change your wireless adapter to be monitor mode by running iwconfig command as follows:

```
$ iwconfig wlan0 mode monitor
```

After that, turn on your wireless adapter again

```
$ ifconfig wlan0 up
```

No if you run iwconfig again, you should see the wireless mode would be in monitor

```
$ iwconfig
```

---
layout: post
title:  "List USB Devices on Your Linux Machine"
categories: vim
date:   2020-05-07 15:00:00 +0700
permalink: /list-usb-devices-linux/
---
# Usage of lsusb

lsusb is a utility for displaying information about USB buses in the system and the devices connected to them

## List USB devices

To list usb devices that's currently active in your computer:

```
lsusb
```

It will give you something similar to:

```
Bus 001 Device 004: ID 138a:0090 Validity Sensors, Inc. 
Bus 001 Device 003: ID 04f2:b5c1 Chicony Electronics Co., Ltd 
```

Lets breakdown what's each columns mean.

- Bus 001 : This is bus number where your device is attached
- Device 004: This is the fourth device attached to Bus 001
- ID 138a:0090: This is the id number given to this device. The format of this number is <manufacture id>:<device id>. To get the list of device id registered in linux, visit [Linux USB site](http://www.linux-usb.org/usb.ids)
- Validity Sensors, Inc.: This is the name of the device.

## List usb ports available

To list all usb ports available in your machine run:

```
find /dev/bus
```

The output will be similar to:

```
/dev/bus
/dev/bus/usb
/dev/bus/usb/002
/dev/bus/usb/002/115
/dev/bus/usb/002/001
/dev/bus/usb/001
/dev/bus/usb/001/088
/dev/bus/usb/001/086
/dev/bus/usb/001/085
/dev/bus/usb/001/004
/dev/bus/usb/001/003
/dev/bus/usb/001/001
```

To get the detail information attached to particular port, use -D option

```
lsusb -D /dev/bus/usb/001/086
```

Output will be similar to:

```
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2516 
  idProduct          0x0020 
.....
```

## See Detail Information of a Device Connected to USB

After you get the manufactur and device id by running the `lsusb` command, now you can show the detail of the device by using `-v` (verbose) option together with -d (vendor) option.

```
lsusb -v -d 138a:0090
```

Hope that's helps


# openwrt-feeds

## Description

  This is the collection of specific packages required by [CreatorDev/openwrt](https://github.com/CreatorDev/openwrt) for Creator Ci40(Marduk) platform
  based upon Imagination's Pistachio SoC.

## Collection of packages for OpenWrt

Package           | Description
:---------------- | -----------------------------
awalwm2m          | Awa LWM2M is an implementation of the OMA Lightweight M2M protocol.
ca8210            | This kernel module is used for cascoda ca8210 transceiver.
cgilua            | This package has been added to use webscripts using lua pages/scripts.
click-apps        | This package contains click applications.
fping             | This program is used to send ICMP echo probes to network hosts, similar to ping.
glog              | This package contains a C++ implementation of the Google logging.
u-boot            | This package is used for u-boot bootloader for pistachio marduk platform.

Command                                         | Description
:---------------------------------------------- | :---------------------------------------
```$ ./scripts/feeds/install awalwm2m```        | Install only the awalwm2m package

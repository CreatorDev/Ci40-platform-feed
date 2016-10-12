# Ci40-platform-feed

## Description

  This is the collection of specific packages required by [CreatorDev/openwrt](https://github.com/CreatorDev/openwrt) for Creator Ci40(Marduk) platform
  based upon Imagination's Pistachio SoC.

## Collection of packages for OpenWrt

Package           | Description
:---------------- | -----------------------------
awalwm2m          | Awa LWM2M is an implementation of the OMA Lightweight M2M protocol.
board-test        | This package contains Ci40 specific board tests.
ca8210            | This kernel module is used for cascoda ca8210 transceiver.
fping             | This program is used to send ICMP echo probes to network hosts, similar to ping.
glog              | This package contains a C++ implementation of the Google logging.
proddata          | This package provides Proddata tool used to read/write/lock OTP.
totd              | This package is used as IPv6 DNS for constrained devices.
u-boot            | This package is used for u-boot bootloader for pistachio marduk platform.

Command                                         | Description
:---------------------------------------------- | :---------------------------------------
```$ ./scripts/feeds install awalwm2m```        | Install only the awalwm2m package

----

## Contributing

We welcome all contributions to this project and we give credit where it's due. Anything from enhancing functionality to improving documentation and bug reporting - it's all good.

For more details about the Contributor's guidelines, refer to the [contributor guide](https://github.com/CreatorKit/creator-docs/blob/master/ContributorGuide.md).

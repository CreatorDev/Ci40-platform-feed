#
# Copyright (C) 2014-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=uccp420wlan
PKG_VERSION:=6.8
PKG_RELEASE=1

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/CreatorDev/uccp420wlan.git
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_MAINTAINER:=Chaitanya Tata <Chaitanya.Tata@imgtec.com>
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/uccp420wlan
  SUBMENU:=Wireless Drivers
  TITLE:=Imagination wireless driver
  DEPENDS:=@TARGET_pistachio +kmod-cfg80211 +kmod-mac80211
  FILES:=$(PKG_BUILD_DIR)/uccp420wlan.$(LINUX_KMOD_SUFFIX)
endef

define KernelPackage/uccp420wlan/description
  Imagination wireless driver
endef

NOSTDINC_FLAGS = \
	-I$(PKG_BUILD_DIR)/inc \
	-I$(STAGING_DIR)/usr/include/mac80211-backport/uapi \
	-I$(STAGING_DIR)/usr/include/mac80211-backport \
	-I$(STAGING_DIR)/usr/include/mac80211/uapi \
	-I$(STAGING_DIR)/usr/include/mac80211 \
	-include backport/backport.h

EXTRA_CFLAGS+=-DMULTI_CHAN_SUPPORT
EXTRA_CFLAGS+=-DDEBUG
EXTRA_CFLAGS+=-DCONFIG_NL80211_TESTMODE

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		ARCH="$(LINUX_KARCH)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		SUBDIRS="$(PKG_BUILD_DIR)" \
		NOSTDINC_FLAGS="$(NOSTDINC_FLAGS)" \
		EXTRA_CFLAGS="$(EXTRA_CFLAGS)" \
		KERNELDIR=$(LINUX_DIR) \
		modules
endef

define KernelPackage/uccp420wlan/install
	$(CP) ./files/* $(1)/
endef

$(eval $(call KernelPackage,uccp420wlan))

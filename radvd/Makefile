include $(TOPDIR)/rules.mk

PKG_NAME:=radvd
PKG_VERSION:=2.11
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/reubenhwk/radvd.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=e3e2b38a0433f680a75dadb394692edec3ea66e3
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk
TARGET_CFLAGS += -std=gnu99

define Package/radvd/Default
  SECTION:=net
  CATEGORY:=Network
  DEFAULT:=n
  DEPENDS:=+libssp +kmod-ipv6
  TITLE:=IPv6 Routing Advertisement
  URL:=https://github.com/reubenhwk/radvd/tree/v2.11
endef

define Package/radvd
  $(call Package/radvd/Default)
  TITLE+= Daemon
endef

define Package/radvd/description
 radvd is the router advertisement daemon for IPv6. It listens to router
 solicitations and sends router advertisements as described in "Neighbor
 Discovery for IP Version 6 (IPv6)" (RFC 4861).  With these advertisements hosts
 can automatically configure their addresses and some other parameters. They also
 can choose a default router based on these advertisements.
endef

define Package/radvdump
  $(call Package/radvd/Default)
  TITLE+= Dumper
endef

define Package/radvdump/description
 radvdump prints out the contents of incoming router advertisements sent by radvd
 or some other software implementing (parts of) "Neighbor Discovery for IP
 Version 6 (IPv6)" (RFC 4861).
endef

define Build/Configure
  $(call Build/Configure/Default,--prefix=/usr/local --sysconfdir=/etc)
endef

define Package/radvd/conffiles
/etc/radvd.conf
endef

define Package/radvd/install
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) ./files/radvd.conf $(1)/etc/radvd.conf
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/radvd $(1)/usr/sbin/
endef

define Package/radvdump/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/radvdump $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,radvd))
$(eval $(call BuildPackage,radvdump))

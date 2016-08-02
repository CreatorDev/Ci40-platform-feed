include $(TOPDIR)/rules.mk
PKG_NAME:=awalwm2m
PKG_VERSION:=0.2.2
#PKG_VERSION:=master
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/FlowM2M/AwaLWM2M.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DWITH_GNUTLS=ON

define Package/awalwm2m
 SECTION:=utils
 CATEGORY:=Utilities
 TITLE:=Awa LWM2M development suite by Imagination Technologies
 DEPENDS:=+libgnutls
endef
define Package/awalwm2m/description
      Awa LWM2M is an implementation of the OMA Lightweight M2M protocol.
endef

define Package/awalwm2m/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/etc/lwm2m
	$(CP) $(PKG_BUILD_DIR)/config/*.bsc $(1)/etc/lwm2m

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/rc.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) files/etc/* $(1)/etc/
	$(CP) files/usr/bin/* $(1)/usr/bin/
endef
$(eval $(call BuildPackage,$(PKG_NAME)))

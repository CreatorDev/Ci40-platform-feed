include $(TOPDIR)/rules.mk

PKG_NAME:=click-apps
PKG_VERSION:=0.1.0

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/IMGCreator/click-apps-for-openwrt.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/click-apps/Default
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Click apps
  DEFAULT:=n
  SUBMENU:=click-apps
endef

define Package/motion-click
  $(call Package/click-apps/Default)
  TITLE:= motion-click app
endef

define Package/click-apps/description
  Click apps
endef

define Build/Compile
	$(call Build/Compile/Default,all)
endef

define Build/Clean
	$(call Build/Compile/Default,clean)
endef

define Package/motion-click/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/motion_click_app $(1)/usr/bin
endef

$(eval $(call BuildPackage,motion-click))

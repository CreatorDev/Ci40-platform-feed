include $(TOPDIR)/rules.mk

PKG_NAME:=webscripts
PKG_VERSION:=0.9.1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/CreatorKit/webscripts.git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DPLATFORM=creator

define Package/webscripts
	SECTION:=utils
	CATEGORY:=Utilities
	DEFAULT:=n
	DEPENDS:= +lua-wsapi-base +cgilua +libubus-lua +lua-coxpcall +libuci-lua
	TITLE:=webscripts
endef

define Package/webscripts/description
	Webscripts to onboard and provision Gateway and Constrained devices
endef

define Build/Compile
	$(call Build/Compile/Default,all)
endef

define Build/Clean
	$(call Build/Compile/Default,clean)
endef

define Package/webscripts/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/data/cgilua $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/www/
	$(INSTALL_DIR) $(1)/www/cgi-bin/
	$(INSTALL_DIR) $(1)/www/css/
	$(INSTALL_DIR) $(1)/www/javascript/
	$(INSTALL_DIR) $(1)/www/image/
	$(INSTALL_DIR) $(1)/etc/lwm2m/
	$(INSTALL_BIN) files/* $(1)/etc/lwm2m/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/var/www/index.html $(1)/www/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/var/www/cgi-bin/* $(1)/www/cgi-bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/var/www/css/* $(1)/www/css/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/var/www/javascript/* $(1)/www/javascript/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/var/www/image/* $(1)/www/image/
endef

$(eval $(call BuildPackage,webscripts))

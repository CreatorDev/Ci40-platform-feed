include $(TOPDIR)/rules.mk
PKG_NAME:=proddata
PKG_VERSION:=0.1.0
#PKG_VERSION:=master
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/Creatordev/proddata.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/proddata
 SECTION:=utils
 CATEGORY:=Utilities
 TITLE:=proddata
endef
define Package/proddata/description
      Proddata tool.
endef

CMAKE_OPTIONS += -DBUILD_TESTS=OFF -DSTAGING_DIR=$(STAGING_DIR)

define Package/proddata/install
	$(INSTALL_DIR) $(1)/usr/bin/
	# rules to install binaries in rootfs
endef
$(eval $(call BuildPackage,$(PKG_NAME)))

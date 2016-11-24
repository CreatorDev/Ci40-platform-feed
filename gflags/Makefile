include $(TOPDIR)/rules.mk
PKG_NAME:=gflags
PKG_VERSION:=v2.1.2
PKG_RELEASE:=1
PKG_LICENSE:=BSD-3c
PKG_LICENSE_FILE:=COPYING.txt

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/gflags/gflags
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1
CMAKE_OPTIONS += -DBUILD_SHARED_LIBS=ON

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/gflags
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libstdcpp
  TITLE:=gflags
endef
define Package/gflags/description
  The gflags package contains a C++ library that implements
  commandline flags processing. It includes built-in support for
  standard types such as string and the ability to define flags in
  the source file in which they are used.
endef

define Package/gflags/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(STAGING_DIR)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(STAGING_DIR)/usr/include/
endef
$(eval $(call BuildPackage,$(PKG_NAME)))

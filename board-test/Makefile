include $(TOPDIR)/rules.mk

PKG_NAME:=board-test
PKG_VERSION:=1.0
PKG_RELEASE:=1
PKG_LICENSE:=BSD-3-Clause

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/CreatorKit/board-test.git
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/board-test
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=board-test
  DEPENDS:= +e2fsprogs
endef

define Package/board-test/install
	$(INSTALL_DIR) $(1)/usr/bin/board_test
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/board_test/test_* $(1)/usr/bin/board_test/
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/usr/bin/board_test/version $(1)/usr/bin/board_test/

	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/board_test_common.sh $(1)/usr/lib/
endef

$(eval $(call BuildPackage,board-test))

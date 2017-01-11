include $(TOPDIR)/rules.mk

PKG_NAME:=u-boot
PKG_RELEASE:=1
PKG_SOURCE_VERSION:=v1.0.4
PKG_VERSION=2015.10-pistachio-$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/CreatorDev/u-boot.git

include $(INCLUDE_DIR)/package.mk

define uboot/pistachio_marduk
  TITLE:=U-Boot for Pistachio Marduk
endef

UBOOTS:= \
	pistachio_marduk

define Package/uboot/template
define Package/uboot-pistachio-$(1)
  SECTION:=boot
  CATEGORY:=Boot Loaders
  TITLE:=$(2)
  DEPENDS:=@TARGET_pistachio
  VARIANT:=$(1)
endef
endef

define Package/uboot/config/template
define Package/uboot-pistachio-$(1)/config
	source "$(CURDIR)/Config.in"
endef
endef

define BuildUBootPackage
	$(eval $(uboot/$(1)))
	$(call Package/uboot/template,$(1),$(TITLE))
	$(call Package/uboot/config/template,$(1))
endef

define Build/Configure
	$(MAKE) -C $(PKG_BUILD_DIR) $(BUILD_VARIANT)_config
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) CROSS_COMPILE=$(TARGET_CROSS)
endef

define Package/uboot/install/Default
	$(CP) \
		$(PKG_BUILD_DIR)/u-boot-pistachio*.img \
		$(BIN_DIR)/
endef

define Package/uboot/install/template
define Package/uboot-pistachio-$(1)/install
	$(call Package/uboot/install/Default,$(1))
	$(if $(CONFIG_PACKAGE_UBOOT_SPL), \
		$(CP) $(PKG_BUILD_DIR)/$(call qstrip,$(CONFIG_PACKAGE_UBOOT_SPL_NAME)) $(BIN_DIR)/)
	$(if $(CONFIG_PACKAGE_UBOOT_ENVIMAGE), \
		$(PKG_BUILD_DIR)/tools/mkenvimage -s $(CONFIG_PACKAGE_UBOOT_ENVIMAGE_SIZE) \
		$(if $(CONFIG_PACKAGE_UBOOT_ENVIMAGE_REDUNDANT),-r) \
		-o $(BIN_DIR)/uboot-env.bin $(CONFIG_PACKAGE_UBOOT_ENVIMAGE_SOURCE))
endef
endef


$(foreach u,$(UBOOTS), \
	$(eval $(call BuildUBootPackage,$(u))) \
	$(eval $(call Package/uboot/install/template,$(u))) \
	$(eval $(call BuildPackage,uboot-pistachio-$(u))) \
)


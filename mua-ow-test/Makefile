include $(TOPDIR)/rules.mk

PKG_NAME:=mua-ow-test
PKG_VERSION:=0.0.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@git.muabaoba.com:depot/mua-ow-test.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/mua-ow-test
  SECTION:=utils
  CATEEGORY:=Mua applications
  TITLE:=Mua OW Test
  DEPENDS:=@TARGET_ramips_mt7688_LinkIt7688
endef

define Package/bridge/description
  Mua test utility for OpenWrt
  Test package; test.
endef

define Build/Configure
	true
endef

define Build/Compile
  $(TARGET_CC) $(TARGET_CFLAGS) $(EXTRA_CFLAGS) -Wall -Werror -o $(PKG_BUILD_DIR)/owt src/main.c
endef

define Package/mtk-linkit-webui/install
	$(INSTALL_DIR) $(1)/usr/local/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/etc/test.conf $(1)/etc/test.conf
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/owt $(1)/usr/local/bin
endef

$(eval $(call BuildPackage,mua-ow-test))

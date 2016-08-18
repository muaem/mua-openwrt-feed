include $(TOPDIR)/rules.mk

PKG_NAME:=mua-ow-hello
PKG_VERSION:=2016-08-18
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@git.muabaoba.com:depot/mua-ow-hello.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/mua-ow-hello
  SECTION:=utils
  CATEEGORY:=Mua applications
  TITLE:=Mua OW Hello
  DEPENDS:=@TARGET_ramips_mt7688_LinkIt7688
endef

define Package/bridge/description
  Mua hello for OpenWrt
  Hello package; hello.
endef

define Build/Configure
	true
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) $(EXTRA_CFLAGS) -Wall -Werror -o $(PKG_BUILD_DIR)/hello $(PKG_BUILD_DIR)/hello.c
endef

define Package/mua-ow-hello/install
	$(INSTALL_DIR) $(1)/usr/local/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/etc/hello.conf $(1)/etc/hello.conf
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/hello $(1)/usr/local/bin
endef

$(eval $(call BuildPackage,mua-ow-hello))

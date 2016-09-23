include $(TOPDIR)/rules.mk

PKG_NAME:=miod
PKG_VERSION:=0.0.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@git.muabaobao.com:depot/package/miod.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/miod
  SECTION:=Mua applications
  CATEEGORY:=Mua applications
  TITLE:=Mua I/O Daemon
  DEPENDS:=+libmraa +libubus +libubox +libblobmsg-json
endef

define Package/miod/description
  Mua hello for OpenWrt
  Hello package; hello.
endef

define Build/Prepare
	$(Build/Prepare/Default)
	$(CP) ./src/* $(PKG_BUILD_DIR)
endef

EXTRA_LDFLAGS += -lmraa -lubus -lubox -lblobmsg_json
TARGET_CFLAGS+= -Wall
MAKE_PATH:=src

define Build/Compile
	$(call Build/Compile/Default, all)
endef

define Package/miod/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/btnd $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ledd $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/nfcd $(1)/usr/bin
	$(CP) ./files/* $(1)/
endef

$(eval $(call BuildPackage,miod))

include $(TOPDIR)/rules.mk

PKG_NAME:=mua-ow-hello
PKG_VERSION:=0.0.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@git.muabaobao.com:depot/mua-ow-hello.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/mua-ow-hello
  SECTION:=utils
  CATEEGORY:=Mua applications
  TITLE:=Mua OW Hello
  DEPENDS:=+libmraa +libupm-pn532 +libubus +libubox
endef

define Package/mua-ow-hello/description
  Mua hello for OpenWrt
  Hello package; hello.
endef

#define Build/Configure
#	true
#endef

define Build/Prepare
	$(Build/Prepare/Default)
	$(CP) ./src/* $(PKG_BUILD_DIR)
endef

EXTRA_LDFLAGS += -lmraa -lupm-pn532 -lubus -lubox
TARGET_CFLAGS+= -Wall
MAKE_PATH:=src

define Build/Compile
	$(TARGET_CC) $(TARGET_CFLAGS) $(EXTRA_CFLAGS) -Wall -Werror -o $(PKG_BUILD_DIR)/hello $(PKG_BUILD_DIR)/hello.c
	#$(call Build/Compile/Default, \
	#	DESTDIR="$(PKG_INSTALL_DIR)" \
	#	CC="$(TARGET_CC)" \
	#	all \
	#	)
	$(call Build/Compile/Default, all)
endef

define Package/mua-ow-hello/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/hello $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/userver $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/uclient $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/mkeyd $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/ks $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/caller $(1)/usr/bin
	$(CP) ./files/* $(1)/
endef

$(eval $(call BuildPackage,mua-ow-hello))

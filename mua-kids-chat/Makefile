include $(TOPDIR)/rules.mk

PKG_NAME:=mua-kids-chat
PKG_VERSION:=0.0.1
PKG_RELEASE=$(PKG_SOURCE_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@git.muabaobao.com:depot/mua-kids-chat.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/mua-kids-chat
	SECTION:=Mua applications
	CATEEGORY:=Mua applications
	TITLE:=Mua Kids Chat
	DEPENDS:=+libspeex +libuuid  +libogg  +libmraa +libubus +libubox +libblobmsg-json +libjson-c +libmosquitto +libpthread +libcares +alsa-lib +libpolarssl +libcurl +libmpg123
	DEFAULT:=y
endef

define Package/mua-kids-chat/description
  Mua Kids Chat
endef

EXTRA_LDFLAGS += -luuid -lspeex -logg  -lmraa -lubus -lubox -lblobmsg_json -ljson-c -lmosquitto -lpthread -lcares -lasound -lpolarssl -lcurl -lmpg123
TARGET_CFLAGS+= -Wall
MAKE_PATH:=src

define Build/Compile
	$(call Build/Compile/Default, all)
endef

define Package/mua-kids-chat/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mua_main_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mua_mqtt_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mua_io_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mua_file_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mua_snd_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mua_msg_service $(1)/usr/bin
	$(CP) ./files/* $(1)
endef

$(eval $(call BuildPackage,mua-kids-chat))

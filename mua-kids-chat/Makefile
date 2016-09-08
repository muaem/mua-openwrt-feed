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
  SECTION:=utils
  CATEEGORY:=Mua applications
  TITLE:=Mua Kids Chat
  DEPENDS:=+libmraa +libubus +libubox +libblobmsg-json +libjson-c +libmosquitto +libpthread +libcares +alsa-lib +libpolarssl +libcurl
endef

define Package/mua-kids-chat/description
  Mua Kids Chat
endef

EXTRA_LDFLAGS += -lmraa -lubus -lubox -lblobmsg_json -ljson-c -lmosquitto -lpthread -lcares -lasound -lpolarssl -lcurl
TARGET_CFLAGS+= -Wall

define Package/mua-kids-chat/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mua_main_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mua_mqtt_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mua_miod_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mua_file_service $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mua_snd_service $(1)/usr/bin
endef

$(eval $(call BuildPackage,mua-kids-chat))

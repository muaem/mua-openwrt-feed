#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libfreefare
PKG_VERSION:=0.4.0
PKG_RELEASE:=1
PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/nfc-tools/libfreefare
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_NAME)-$(PKG_VERSION)

PKG_LICENSE:=LGPL-2.1
PKG_MAINTAINER:=Robbie Cao <robbie.cao@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/libfreefare/Default
	TITLE:=A convenience API for NFC cards manipulations on top of libnfc
	URL:=http://nfc-tools.org/
endef

define Package/libfreefare
	$(call Package/libfreefare/Default)
	SECTION:=libs
	CATEGORY:=Libraries
	DEPENDS:=+libnfc +libopenssl
endef

define Package/libfreefare/description
	libfreefare provides a convenient API for MIFARE card manipulations.

endef

define Package/nfc-freefare-utils
$(call Package/libfreefare/Default)
SECTION:=utils
CATEGORY:=Utilities
DEPENDS:=+libfreefare
endef

define Package/nfc-utils/description
	Provide some examples shared functions for libfreefare

endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libfreefare.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libfreefare.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libfreefare/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libfreefare.so.* $(1)/usr/lib/
endef

define Package/nfc-freefare-utils/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-classic-format $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-classic-read-ndef $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-classic-write-ndef $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-access $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-create-ndef $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-ev1-configure-ats $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-ev1-configure-default-key $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-ev1-configure-random-uid $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-format $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-info $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-read-ndef $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-desfire-write-ndef $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/mifare-ultralight-info $(1)/usr/bin/

endef

$(eval $(call BuildPackage,libfreefare))
$(eval $(call BuildPackage,nfc-freefare-utils))

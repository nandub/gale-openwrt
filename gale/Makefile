# 
# Copyright (C) 2006-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gale
PKG_VERSION:=0.1.0
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/nandub/gale/archive
PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_MD5SUM:=9e1f9304596464850d847911c961a891

include $(INCLUDE_DIR)/package.mk

define Package/gale
 SECTION:=app
 CATEGORY:=Application
 TITLE:=Secure Instant Messaging Software
 URL:=http://www.gale.org
 DEPENDS:=+adns +gc +libopenssl
endef

define Package/gale/description
	Gale is a instant messaging software
endef

define Build/Configure
	(cd "$(PKG_BUILD_DIR)"; ./bootstrap );
	$(call Build/Configure/Default)
endef

CONFIGURE_VARS+= \
	ac_cv_lib_gc_GC_malloc=yes \
	ac_cv_lib_adns_adns_init=yes

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		all
endef

define Build/Install
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \ 
		install
endef

define Package/gale/install
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/include/gale
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/gale/auth/trusted
	$(INSTALL_DIR) $(1)/etc/gale/auth/private
	$(INSTALL_DIR) $(1)/etc/gale/auth/local
	$(INSTALL_DIR) $(1)/etc/gale/auth/cache
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/gale/*.h $(1)/usr/include/gale/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
	$(CP) $(PKG_INSTALL_DIR)/etc/gale/auth/truested/ROOT $(1)/etc/gale/auth/trusted
endef

$(eval $(call BuildPackage,gale))

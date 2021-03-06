# 
# Copyright (C) 2006-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gc
PKG_VERSION:=7.2d
_PKG_VERSION=7.2
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://www.hpl.hp.com/personal/Hans_Boehm/gc/gc_source
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(_PKG_VERSION)
PKG_MD5SUM:=91340b28c61753a789eb6077675d87d2

include $(INCLUDE_DIR)/package.mk

define Package/gc
 SECTION:=libs
 CATEGORY:=Libraries
 TITLE:=A garbage collector for C and C++
 URL:=http://www.hpl.hp.com/personal/Hans_Boehm/gc
 DEPENDS:=+libstdcpp +libpthread
endef

define Package/gc/description                                                
	A garbage collector for C and C++
endef

define Build/Configure
	$(call Build/Configure/Default)
endef

CONFIGURE_ARGS+= \
	--disable-debug \
	--disable-dependency-tracking \
	--enable-cplusplus

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)"
endef

define Build/Install
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		install
endef

define Package/gc/install
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/include/gc
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/gc/*.h $(1)/usr/include/gc/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
endef

$(eval $(call BuildPackage,gc))

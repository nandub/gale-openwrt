# 
# Copyright (C) 2006-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=adns
PKG_VERSION:=1.4
PKG_RELEASE:=1

PKG_SOURCE_URL:=http://www.chiark.greenend.org.uk/~ian/adns/ftp
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_MD5SUM:=88bc7bbf3f62a8d4fb186b8f72ead853

include $(INCLUDE_DIR)/package.mk

define Package/adns
 SECTION:=libs
 CATEGORY:=Libraries
 TITLE:=adns
 URL:=http://www.chiark.greenend.org.uk/~ian/adns
endef

define Package/adns/description                                                
  adns is a resolver library for C and C++ programs, and a collection of useful DNS resolver utilities.
endef

define Package/adns/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/*.a $(1)/usr/lib/
endef

define Package/adns/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/*.h $(1)/usr/include/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/*.o $(1)/usr/lib/
endef

$(eval $(call BuildPackage,adns))

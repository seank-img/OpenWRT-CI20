#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lowpan-tools
PKG_VERSION:=0.3.1
PKG_REV:=1c2d8674cc6f4b1166a066e8822e295c105ae7a2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://github.com/linux-wpan/lowpan-tools.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_PROTO:=git
#PKG_SOURCE_URL:=http://wpan.cakelab.org/releases/
#PKG_MD5SUM:=37575523d1543e06b11295f03a891fa7

include $(INCLUDE_DIR)/package.mk

define Package/lowpan-tools
  SECTION:=net
  CATEGORY:=Network
  TITLE:=This is a set of utils to manage the Linux LoWPAN stack
  URL:=http://wpan.cakelab.org/
  DEPENDS:= +libnl
endef

define Build/Configure
	cd $(PKG_BUILD_DIR); sh ./autogen.sh
	$(call Build/Configure/Default)
endef

define Package/lowpan-tools/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/iz $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/izattach $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/izcoordinator $(1)/usr/sbin/

endef

$(eval $(call BuildPackage,lowpan-tools))

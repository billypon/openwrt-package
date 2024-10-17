#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.


include $(TOPDIR)/rules.mk

PKG_NAME:=n2n
PKG_VERSION:=3.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/ntop/n2n/archive/$(PKG_VERSION)
PKG_HASH:=25fcabba7bfcf25f4c9cd7fecc7ce11de48beb0b0f3506053d8485604ea8f50d

include $(INCLUDE_DIR)/package.mk

define Package/n2n
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=VPN tunneling daemon
  URL:=http://www.ntop.org/n2n/
  DEPENDS:=libpthread +libopenssl
endef

define Build/Compile
	cd $(PKG_BUILD_DIR) && ./autogen.sh && ./configure
	$(MAKE) CC="$(TARGET_CC)" -C $(PKG_BUILD_DIR)
endef


define Package/n2n/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/edge $(1)/usr/sbin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/supernode $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,n2n))

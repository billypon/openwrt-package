#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tig
PKG_VERSION:=2.5.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/jonas/tig/releases/download/$(PKG_NAME)-$(PKG_VERSION)/
PKG_MD5SUM:=f655cc1366fc10058a2bd505bb88ca78e653ff7526c1b81774c44b9d841210e3
PKG_CAT:=zcat

PKG_BUILD_DIR:=$(BUILD_DIR)/tig-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=libncurses libiconv

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

define Package/tig
	SECTION:=devel
	CATEGORY:=Development
	TITLE:=Console Git repository viewer
	URL:=http://jonas.nitro.dk/tig/releases/
	DEPENDS:=+git +libncursesw
endef

define Package/tig/description
	Tig is a git repository browser that additionally can act as a pager for output
	from various git commands.
endef

CONFIGURE_ARGS+= \
	--with-libiconv="$(ICONV_PREFIX)"

define Package/tig/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/tig $(1)/usr/bin/
endef

$(eval $(call BuildPackage,tig))

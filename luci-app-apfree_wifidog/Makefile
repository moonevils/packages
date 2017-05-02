# call BuildPackage - OpenWrt buildroot signature
#    Copyright © 2017 gigibox zhangzengfei@kunteng.org
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License along
#    with this program; if not, write to the Free Software Foundation, Inc.,
#    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#
#    The full GNU General Public License is included in this distribution in
#    the file called "COPYING".

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-apfree_wifidog
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_LICENSE:=GPL-3.0

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-apfree_wifidog
	SECTION:=luci
	CATEGORY:=LuCI
	SUBMENU:=3. Applications
	TITLE:=LuCI support for ApFree WifiDog
	DEPENDS:=+luci-base
	PKGARCH:=all
endef

define Package/luci-app-apfree_wifidog/description
	This package allows you to configure wifidog using LuCI.
endef

define Build/Compile
endef

define Package/luci-app-apfree_wifidog/postinst
#!/bin/sh
UCI_DEF_FILE=90_luci_xkcptun
if [ -z "$${IPKG_INSTROOT}" ]; then
	if [ -f /etc/uci-defaults/$UCI_DEF_FILE ]; then
		( . /etc/uci-defaults/$UCI_DEF_FILE ) && \
		rm -f /etc/uci-defaults/$UCI_DEF_FILE
	fi
	rm -rf /tmp/luci-indexcache /tmp/luci-modulecache
fi
exit 0
endef

define Package/luci-app-apfree_wifidog/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	$(CP) ./luasrc/* $(1)/usr/lib/lua/luci
	$(CP) ./root/* $(1)/
endef

$(eval $(call BuildPackage,luci-app-apfree_wifidog))
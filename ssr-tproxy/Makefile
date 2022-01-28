#
# Copyright (C) 2018-2021 honwen <https://github.com/honwen>
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ssr-tproxy
PKG_VERSION:=2022-01-16
PKG_RELEASE:=1.0

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/ssr-tproxy
	SECTION:=net
	CATEGORY:=Network
	TITLE:=SSR-TPROXY
	DEPENDS:=+dnsmasq-full +ipset +curl +ipt2socks +dns2socks +ssr-native
	PKGARCH:=all
endef

define Package/ssr-tproxy/description
	ssr-tproxy include gfwlist
endef

define Build/Compile
endef

#define Package/ssr-tproxy/conffiles
#	/etc/ssr-tproxy/custom.conf
#	/etc/ssr-tproxy/chnroute.txt
#	/etc/ssr-tproxy/gfwlist.gz
#endef

define Package/ssr-tproxy/install
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/ssr-tproxy.conf $(1)/etc/config/ssr-tproxy
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/ssr-tproxy.init $(1)/etc/init.d/ssr-tproxy
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/uci-defaults $(1)/etc/uci-defaults/ssr-tproxy
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/gfwupd $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/ssr-tproxy
	$(INSTALL_DATA) ./files/data/gfwlist.conf $(1)/etc/ssr-tproxy
	$(INSTALL_DATA) ./files/data/custom.conf $(1)/etc/ssr-tproxy
endef

$(eval $(call BuildPackage,ssr-tproxy))

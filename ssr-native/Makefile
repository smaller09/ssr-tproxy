include $(TOPDIR)/rules.mk

PKG_NAME:=ssr-native
PKG_VERSION:=0.9.2
PKG_RELEASE:=$(AUTORELEASE)
PKG_HASH:=0258ee972bc0e55fb1a3966b35425558464d2ef8bb6c4f36183788f6b7f1178c

#PKG_SOURCE_URL:=https://github.com/ShadowsocksR-Live/shadowsocksr-native/archive/refs/tags/$(PKG_VERSION).tar.gz
#PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
#PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(BUILD_VARIANT)/

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_USE_MIPS16:=0
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DEPENDS:=libsodium mbedtls libuv libjson-c libhttp-parser
 
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/ssr-native
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Lightweight Secured Socks5 Proxy
	URL:=https://github.com/ShadowsocksR-Live/shadowsocksr-native
	DEPENDS:=+libuv +libmbedtls +libsodium +libjson-c +libhttp-parser 
endef

define Package/ssr-native/description
Shadowsocksr-libuv-native is a lightweight secured socks5 proxy for embedded devices and low end boxes.
endef

CMAKE_OPTIONS += -DBUILD_SHARED_AND_STATIC_LIBS=On\
    -DCMAKE_INSTALL_PREFIX=/usr/bin

define Package/ssr-native/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ssr-client $(1)/usr/bin
	$(INSTALL_DATA) ./file/ssr-n.json $(1)/etc/
endef

$(eval $(call BuildPackage,ssr-native))

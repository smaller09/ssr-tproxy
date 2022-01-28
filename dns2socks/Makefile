include $(TOPDIR)/rules.mk

PKG_NAME:=dns2socks
PKG_VERSION:=2.1
PKG_RELEASE:=b20dcfb932b4be40342779b70beeaf59e212903b

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/qiuzi/dns2socks.git
PKG_SOURCE_VERSION:=$(PKG_RELEASE)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_LICENSE:=GPL-3.0
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_HASH:=4dc35a2a40b464b77a8d528d56959c1089faf2409bb5549cd2df94a83ebdcde0 

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/dns2socks
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  TITLE:=The utility to resolve DNS requests via a SOCKS5 tunnel.
  URL:=https://sourceforge.net/projects/dns2socks/
  DEPENDS:=+libpthread
endef

define Package/dns2socks/description
  This is a utility to resolve DNS requests via a SOCKS5 tunnel and caches the answers.
endef

define Build/Compile
	$(TARGET_CC) \
	$(TARGET_CFLAGS) \
	$(TARGET_CPPFLAGS) \
	$(FPIC) \
	-o $(PKG_BUILD_DIR)/$(PKG_NAME) \
	$(PKG_BUILD_DIR)/DNS2SOCKS.c \
	$(TARGET_LDFLAGS) -pthread
endef

define Package/dns2socks/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(PKG_NAME) $(1)/usr/bin/dns2socks
endef

$(eval $(call BuildPackage,dns2socks))

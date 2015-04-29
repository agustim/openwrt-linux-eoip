#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=linux-eoip
PKG_VERSION:=0.5
PKG_RELEASE:=1


PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://linux-eoip.googlecode.com/files/
PKG_MD5SUM:=b2a9746f9ae352f2c495422cb19900d8
PKG_USE_MIPS16:=0


PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/linux-eoip/Default
  TITLE:=Mikrotik-compatible userspace EoIP tunnel
  URL:=http://code.google.com/p/linux-eoip/
endef

define Package/linux-eoip
  $(call Package/linux-eoip/Default)
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+kmod-tun +libpthread +liblzo
  TITLE+= (command line)
endef

define Package/linux-eoip/description
	MakeFile para gerar o pacote Linux-EoIP para o firmware openwrt;
	Fork Brasileiro;
	Integração de túneis EoIP Mikrotik e linux.
	
endef

TARGET_CFLAGS += -std=gnu99

CONFIGURE_ARGS += \
	--with-kernel="$(LINUX_DIR)" \
	--with-zlib="$(STAGING_DIR)/usr" \
	--with-lzo-include="$(STAGING_DIR)/usr/include/lzo"

define Package/linux-eoip/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/eoip $(1)/usr/bin/
endef

$(eval $(call BuildPackage,linux-eoip))

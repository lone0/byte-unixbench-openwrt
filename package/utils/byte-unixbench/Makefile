#
# Copyright (C) 2006-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=byte-unixbench
PKG_VERSION:=5.1.3
PKG_RELEASE:=1

#https://github.com/kdlucas/byte-unixbench/archive/refs/tags/v5.1.3.tar.gz

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/kdlucas/$(PKG_NAME)/archive/refs/tags/
PKG_HASH:=3a6bb00f270a5329682dff20fd2c1ab5332ef046eb54a96a0d7bd371005d31a3
PKG_MAINTAINER:=lone.2004@gmail.com

PKG_LICENSE:=GPL-2.0

PKG_CHECK_FORMAT_SECURITY:=0

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+perlbase-posix +perl +perlbase-time +perlbase-io +perlbase-findbin +coreutils-od
  TITLE:=Unix benchmark suite
  URL:=https://github.com/kdlucas/byte-unixbench/
endef

define Package/$(PKG_NAME)/description
	UnixBench is a simple benchmark whose purpose is to provide a basic indicator of the performance of a Unix-like system.
endef

define Build/Configure
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/UnixBench \
		$(TARGET_CONFIGURE_OPTS) \
		prefix="$(PKG_INSTALL_DIR)/usr"
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/unixbench
	cp -pPR $(PKG_BUILD_DIR)/UnixBench/* $(1)/usr/lib/unixbench
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

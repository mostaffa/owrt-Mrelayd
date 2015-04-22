#
# Copyright (C) 2010-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mrelayd
PKG_VERSION:=2015-04-22
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/DRTEK/mrelayd.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=V1

PKG_MAINTAINER:=MK <mkoseoglu@drtek.com.tr>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mrelayd
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  TITLE:=Multi Transparent routing / relay daemon
  DEPENDS:=+libubox
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include

define Package/mrelayd/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mrelayd $(1)/usr/sbin/mrelayd
	$(INSTALL_DIR) $(1)/etc/hotplug.d/iface
	$(INSTALL_DATA) ./files/relay.hotplug $(1)/etc/hotplug.d/iface/30-relay
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/relay.init $(1)/etc/init.d/relayd
endef

$(eval $(call BuildPackage,mrelayd))

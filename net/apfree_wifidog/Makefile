include $(TOPDIR)/rules.mk

PKG_NAME:=apfree_wifidog													# 包名
PKG_VERSION:=2.03.1061														# 包版本
PKG_RELEASE=1															    # Makefile版本


PKG_LICENSE:=GPL-2.0													    # 包许可文件
PKG_MAINTAINER:=Dengfeng Liu<liudengfeng@kunteng.org>						# 维持者
PKG_LICENSE_FILES:=COPYING													# 许可协议文件

PKG_SOURCE_PROTO:=git														# 使用下载协议
PKG_SOURCE_URL:=https://github.com/liudf0716/apfree_wifidog.git				# 用于下载源码的地址
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)								# 下载目录，下载协议svn或git必须指定
PKG_SOURCE_VERSION:=$(PKG_VERSION)											# 下载源码版本，下载协议git时必须指定
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz			# 原始代码文件名
PKG_MIRROR_HASH:=40293b58d4be4ade84dc826a4a01c30a8ba97198c8040b0062fa8db0f8379987

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1                                                              # 表示使用自己的make install
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)			# 编译包安装目录

include $(INCLUDE_DIR)/package.mk											# 普通包定义宏
include $(INCLUDE_DIR)/cmake.mk												# 使用cmake编译

define Package/$(PKG_NAME)
  SUBMENU:=Captive Portals
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+zlib +iptables-mod-extra +iptables-mod-ipopt +kmod-ipt-nat +iptables-mod-nat-extra \
           +libpthread +libopenssl +libjson-c +ipset +libip4tc +libevent2 +libevent2-openssl \
		   +fping +libmosquitto +libuci
  TITLE:=Apfree's wireless captive portal solution
  URL:=http://www.kunteng.org
endef

define Package/$(PKG_NAME)/description
	The ApFree Wifidog project is a complete and embeddable captive
	portal solution for wireless community groups or individuals
	who wish to open a free Hotspot while still preventing abuse
	of their Internet connection.
    It's enhanced wifidog
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/wifidog $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/wdctl $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libhttpd.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) ./files/wdping $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/wifidog-msg.html $(1)/etc/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/wifidog-redir.html $(1)/etc/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/wifidog-redir.html.front $(1)/etc/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/wifidog-redir.html.rear $(1)/etc/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/authserver-offline.html $(1)/etc/ 
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/internet-offline.html $(1)/etc/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/wifidog.init $(1)/etc/init.d/wifidog
	$(INSTALL_DIR) $(1)/etc/config
	$(CP) ./files/wifidog.conf $(1)/etc/config/wifidog
	$(CP) ./files/apfree.* $(1)/etc/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))

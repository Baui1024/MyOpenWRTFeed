# Copyright (C) 2017 Onion Corporation
#
# Author: Lazar Demin  <lazar@onion.io>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
PKG_NAME:=python-spidev
PKG_VERSION:=4.0.1
PKG_RELEASE:=3


PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_URL:=https://github.com/Baui1024/python-spidev.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/python3-spidev
	SECTION:=onion
	CATEGORY:=Onion
	SUBMENU:=Libraries
	TITLE:=Python3 module with object that implements SPI transactions
	DEPENDS:=+python3-base
endef

define Package/python3-spidev/description
Python3 module with object that implements SPI transactions
endef


TARGET_CFLAGS += $(FPIC)
TARGET_LIBS += -l m

PYTHON3_VERSION = 3.9
TARGET_PYTHON3_INC += "-I$(STAGING_DIR)/usr/include/python$(PYTHON3_VERSION)/"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) wipe
	
	$(MAKE) -C $(PKG_BUILD_DIR) \
	CC="$(TARGET_CC)" \
	CFLAGS="$(TARGET_CFLAGS)" \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	LIB="$(TARGET_LIBS)" \
	PYTHON_VERSION="$(PYTHON3_VERSION)" \
	PYINC="$(TARGET_PYTHON3_INC)"
endef


define Package/python3-spidev/install
	# install the python module
	$(INSTALL_DIR) $(1)/usr/lib/python$(PYTHON3_VERSION)
	$(CP)   $(PKG_BUILD_DIR)/lib/python$(PYTHON3_VERSION)/spidev.so $(1)/usr/lib/python$(PYTHON3_VERSION)
endef


$(eval $(call BuildPackage,python3-spidev))

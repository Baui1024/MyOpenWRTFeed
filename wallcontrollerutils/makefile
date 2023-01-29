include $(TOPDIR)/rules.mk
PKG_NAME:=python-wallcontrollerutils
PKG_VERSION:=0.0.2
PKG_RELEASE:=1


PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_URL:=https://github.com/Baui1024/wallcontrollerutils.git

PKG_SOURCE_SUBDIR:=$(PKG_NAME)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/python3-wallcontrollerutils
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=Python3 module for fast conversion
	DEPENDS:=+python3-base
endef

define Package/python3-wallcontrollerutils/description
Python3 module module that converts RGB888 to RGB565
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



define Package/python3-wallcontrollerutils/install
	# install the python module
	$(INSTALL_DIR) $(1)/usr/lib/python$(PYTHON3_VERSION)
	$(CP)   $(PKG_BUILD_DIR)/lib/python$(PYTHON3_VERSION)/wallcontrollerutils.so $(1)/usr/lib/python$(PYTHON3_VERSION)
endef


$(eval $(call BuildPackage,python3-wallcontrollerutils))


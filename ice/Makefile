include $(TOPDIR)/rules.mk

PKG_NAME:=intel_ice
PKG_RELEASE=1.8.8

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/intel_ice
  SUBMENU:=Network Devices
  TITLE:=Linux* Base Drivers for Intel(R) Ethernet Network
  DEPENDS:=@PCI_SUPPORT +kmod-ptp
  FILES:=\
	$(PKG_BUILD_DIR)/auxiliary.ko \
	$(PKG_BUILD_DIR)/ice.ko
  AUTOLOAD:=$(call AutoLoad,35,ice)
  PROVIDES:=kmod-intel_ice
endef

define KernelPackage/intel_ice/description
 Kernel modules for Intel E810, E822, E823 Intel Ethernet devices.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) NEED_AUX_BUS=2 \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,intel_ice))

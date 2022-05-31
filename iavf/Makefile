include $(TOPDIR)/rules.mk

PKG_NAME:=intel_iavf
PKG_RELEASE=4.4.2.1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/intel_iavf
  SUBMENU:=Network Devices
  TITLE:=Intel(R) Ethernet Adaptive Virtual Function support
  DEPENDS:=@PCI_SUPPORT  +kmod-ptp
  FILES:=\
	$(PKG_BUILD_DIR)/auxiliary.ko \
	$(PKG_BUILD_DIR)/iavf.ko
  AUTOLOAD:=$(call AutoProbe,iavf)
  PROVIDES:=kmod-intel_iavf
endef

define KernelPackage/intel_iavf/description
 Kernel modules for Intel XL710,
	  X710, X722, XXV710, V710, E810, E822, E823 and all devices advertising support for
	  Intel Ethernet Adaptive Virtual Function devices.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) NEED_AUX_BUS=2 \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,intel_iavf))

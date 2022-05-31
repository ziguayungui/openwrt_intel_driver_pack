include $(TOPDIR)/rules.mk

PKG_NAME:=intel_ixgbevf
PKG_RELEASE=4.15.1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/intel_ixgbevf
  SUBMENU:=Network Devices
  TITLE:=Intel(R) 82599 Virtual Function Ethernet support
  DEPENDS:=@PCI_SUPPORT +kmod-intel_ixgbe
  FILES:=\
	$(PKG_BUILD_DIR)/ixgbevf.ko
  AUTOLOAD:=$(call AutoLoad,35,ixgbevf)
  PROVIDES:=kmod-intel_ixgbevf
endef

define KernelPackage/intel_ixgbevf/description
 Kernel modules for Intel(R) 82599 Virtual Function Ethernet adapters.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,intel_ixgbevf))

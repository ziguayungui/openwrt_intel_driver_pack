include $(TOPDIR)/rules.mk

PKG_NAME:=intel_ixgbe
PKG_RELEASE=5.15.2

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/intel_ixgbe
  SUBMENU:=Network Devices
  TITLE:=Intel(R) 82598/82599 PCI-Express 10 Gigabit Ethernet support
  DEPENDS:=@PCI_SUPPORT +kmod-ptp
  FILES:=\
	$(PKG_BUILD_DIR)/ixgbe.ko
  AUTOLOAD:=$(call AutoLoad,35,ixgbe)
  PROVIDES:=kmod-intel_ixgbe
endef

define KernelPackage/intel_ixgbe/description
 Kernel modules for Intel(R) 82598/82599, X520, X540, X550, X552, X553 PCI-Express 10 Gigabit Ethernet adapters.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,intel_ixgbe))

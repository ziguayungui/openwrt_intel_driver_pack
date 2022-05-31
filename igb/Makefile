include $(TOPDIR)/rules.mk

PKG_NAME:=intel_igb
PKG_RELEASE=5.10.2

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/intel_igb
  SUBMENU:=Network Devices
  TITLE:=Intel(R) 82575/82576 PCI-Express Gigabit Ethernet support
  DEPENDS:=@PCI_SUPPORT +kmod-ptp
  FILES:=\
	$(PKG_BUILD_DIR)/igb.ko
  AUTOLOAD:=$(call AutoLoad,35,igb)
  PROVIDES:=kmod-intel_igb
endef

define KernelPackage/intel_igb/description
 Kernel modules for Intel(R) 82575/82576 PCI-Express Gigabit Ethernet adapters.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,intel_igb))

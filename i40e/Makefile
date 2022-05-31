include $(TOPDIR)/rules.mk

PKG_NAME:=intel_i40e
PKG_RELEASE=2.19.3

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/intel_i40e
  SUBMENU:=Network Devices
  TITLE:=Intel(R) Ethernet Controller XL710 Family support
  DEPENDS:=@PCI_SUPPORT +kmod-ptp
  FILES:=\
	$(PKG_BUILD_DIR)/auxiliary.ko \
	$(PKG_BUILD_DIR)/i40e.ko
  AUTOLOAD:=$(call AutoProbe,i40e)
  PROVIDES:=kmod-intel_i40e
endef

define KernelPackage/intel_i40e/description
 Kernel modules for Intel(R) Ethernet Controller XL710 , X722Family 40 Gigabit Ethernet adapters.
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) NEED_AUX_BUS=2 \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,intel_i40e))

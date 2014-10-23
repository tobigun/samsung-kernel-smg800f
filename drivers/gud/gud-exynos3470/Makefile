#
# Makefile for the kernel mobicore drivers
#
##################################
#mobicore_security_team_add
##################################
GUD_ROOT_FOLDER := drivers/gud/gud-exynos3470
##################################
# add our modules to kernel.
obj-$(CONFIG_MOBICORE_API) += mcKernelApi.o
obj-$(CONFIG_MOBICORE_DRIVER) += mcDrvModule.o

mcDrvModule-objs := MobiCoreDriver/logging.o \
		MobiCoreDriver/ops.o \
		MobiCoreDriver/mem.o \
		MobiCoreDriver/api.o \
		MobiCoreDriver/pm.o \
		MobiCoreDriver/main.o

mcKernelApi-objs := MobiCoreKernelApi/main.o \
		MobiCoreKernelApi/clientlib.o \
		MobiCoreKernelApi/device.o \
		MobiCoreKernelApi/session.o \
		MobiCoreKernelApi/connection.o
		
obj-$(CONFIG_SECURE_OS_CONTROL) += sec-os-ctrl/		

# Release mode by default
ccflags-y := -DNDEBUG 
ccflags-y += -include$(srctree)/$(GUD_ROOT_FOLDER)/build_tag.h
ccflags-y += -Wno-declaration-after-statement

ccflags-$(CONFIG_MOBICORE_DEBUG) += -DDEBUG
ccflags-$(CONFIG_MOBICORE_VERBOSE) += -DDEBUG_VERBOSE

# Choose one platform from the folder
ifeq ($(MOBICORE_PLATFORM), ARM_VE_A9X4_QEMU)
    ccflags-y += -DMC_NETLINK_COMPAT
endif

ifeq ($(MOBICORE_PLATFORM), MSM8974_SURF_STD)
    ccflags-y += -DMC_NETLINK_COMPAT_V37
endif

ifeq ($(MOBICORE_PLATFORM), EXYNOS_5422_STD)
    ccflags-y += -DMC_NETLINK_COMPAT_V37
endif

ifeq ($(MOBICORE_PLATFORM), EXYNOS_5430_STD)
    ccflags-y += -DMC_NETLINK_COMPAT_V37
endif

# Include platform folder
ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreDriver/platforms/EXYNOS_3470_STD
# MobiCore Driver includes
ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreDriver/public
# MobiCore KernelApi required incldes
ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreKernelApi/include
ccflags-y += -I$(GUD_ROOT_FOLDER)/MobiCoreKernelApi/public

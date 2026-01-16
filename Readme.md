# Kickpi-K1
DTS and Patch for Kickpi-K1 Rk3568 Mainline 

Converted from 5.1 vendor dts/dtsi for kernel 6.18

Patch uses Rock-3a uboot configuration for Armbian to create the kickpi-k1.conf.
For Armbian build, place the patch in build/userpatches/kernel/archive/rockchip64-6.18 (change for the current kernel version).


# Working
* EMMC for boot with Armbian install
* MicroSD for boot and with Armbian
* SATA
* USB
* USB-C
* HDMI
* HDMI Audio
* M.2
* MiniPCI (not tested)
* GIPO (not tested)
* Mic Onboard
* Headset and Mic
* Wifi
* Ethernet 0
* Ethernet 1
* Power and Heartbeat LED
* GPU
* JTAG Debug
* Bluetooth

# Not Working
* Mipi-csi camara
* NPU
* Other display connections
* SIM card (unknown)
* Gyroscope (not on board?)


Example build command

./compile.sh build BOARD=kickpi-k1 BRANCH=edge BUILD_DESKTOP=yes BUILD_MINIMAL=no DESKTOP_APPGROUPS_SELECTED='browsers desktop_tools internet multimedia remote_desktop' DESKTOP_ENVIRONMENT=xfce DESKTOP_ENVIRONMENT_CONFIG_NAME=config_base INSTALL_HEADERS=yes KERNEL_CONFIGURE=no KERNEL_GIT=shallow RELEASE=noble

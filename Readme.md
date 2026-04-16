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
* NPU (not tested - not supported by 6.19RC4)
* Fan Header
* RTC Battery connection (not fully tested)

# Not Working
* Mipi-csi camara (need adapter or supported 40 pin camera)
* Other display connections
* SIM card (unknown)
* Gyroscope (not on board?)
* Headset auto detection (not wired?)
* Speaker Connector (not tested)


Example build command

./compile.sh build BOARD=kickpi-k1 BRANCH=edge BUILD_DESKTOP=yes BUILD_MINIMAL=no DESKTOP_APPGROUPS_SELECTED='browsers desktop_tools internet multimedia remote_desktop' DESKTOP_ENVIRONMENT=xfce DESKTOP_ENVIRONMENT_CONFIG_NAME=config_base INSTALL_HEADERS=yes KERNEL_CONFIGURE=no KERNEL_GIT=shallow RELEASE=noble

#Enable NPU in Kernel
CONFIG_ACCEL_ROCKET=y
CONFIG_ACCEL_ROCKET_RK3568=y
Not supported for rk3568 as of 6.19 RC4.

#Armbian-Install Not Detecting EMMC
*As of 4-15-2026 Armbian Edge armbian-install may not detect the emmc. It seems to look for specific type and wont work if the emmc has been wiped.
*Possible fix.
**Boot from SD
**Wipe the emmc and nvme
**Lable the disks and create a partiion
**Partprobe
**Run armbian-install
*
sudo wipefs -a /dev/mmcblk0
sudo wipefs -a /dev/nvme0n1

sudo parted /dev/mmcblk0 mklabel gpt
sudo parted /dev/mmcblk0 mkpart primary ext4 0% 100%

sudo parted /dev/nvme0n1 mklabel gpt
sudo parted /dev/nvme0n1 mkpart primary ext4 0% 100%

sudo partprobe /dev/mmcblk0
sudo partprobe /dev/nvme0n1
*

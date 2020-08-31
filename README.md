# MI9-Nethunter-Project
<br> Warning: This kernel is intended for hacker technology learning and communication, not for illegal use, all behaviors and responsibilities have nothing to do with me!   [简体中文](https://github.com/shandongtlb/MI9-Nethunter-Project/blob/master/README_ZH.md)

<br> This kernel is modified based on CAF kernel source and is suitable for MIUI12. Basically, the nethunter official website supports all the functions of the mobile phone and has solved all known problems. You can download and use the kernel from release.
<br> Now, this is my [kernel source](https://github.com/shandongtlb/msm-4.14)

<br> This patch supports all Linux devices based on the 4.14.X kernel version [Nethunter kernel patch](https://github.com/shandongtlb/MI9-Nethunter-Project/blob/master/MI9-nethunter-4.14.patch)
<br> Click [here](https://github.com/shandongtlb/MI9-Nethunter-Project/releases) to download Mi9-nethunter-kernel-release
<br> The last version: V19 20200831 4.14.195 LTS
## Kernel function
### Nethunter function (You can use the patch I provided to implement WIFI inject and HID, and you also need to configure defconfig yourself [patch](https://github.com/shandongtlb/MI9-Nethunter-Project/blob/master/MI9-nethunter-4.14.patch))
<br>  WIFI Injection IEEE80211 and support 2.4GHZ & 5GHZ
<br>  Support otg MTKMT7601U rt28xx/307x ar9170 rtl8187/8 ZD1201USB.....
<br>  New rtl88xxau driver support form https://github.com/aircrack-ng/rtl8812au (default disable, you should build own)
<br>  HID attack and support DuckyHID
<br>  DriveDroid support
<br>  SYSVIPC (now you can run postgresql normally)
<br>  USB RNDIS
<br>  USB RTL8150/2/3 based ethernet device support
<br>  USB/UART bluetooth device
<br>  RTL-SDR, AirSpy, Hackrf
<br>  USB serial (now it supports ch340 and pl2303)
<br>  Wireless extension compatible (now you can use `iwconfig` and set monitor mode)
<br>  Enable Qualcomm WiFi monitor mode, now you can set your network card "wlan0" to monitor mode(No injection support)
### Release kernel Characteristic
<br>  Update to 4.14.195
<br>  Merge android-4.14-q from googlesource
<br>  Merge tag 'LA.UM.8.1.r1-15800-sm8150.0' for kernel tree, WLAN, data_rmnet
<br>  Add BBRv2 and set default
<br>  Add 810mhz gpu freq
<br>  Add klapse5.0
<br>  Add Audio control
<br>  Add zen iosched and zen is default
<br>  Add dynamic fsync
<br>  Set ddr 2133MHZ
<br>  Add and upstream simple LMK
<br>  Add CPU input boost
<br>  Unlock battery charge capacity
<br>  Enable MTP 900ma force fast charge
<br>  Set zram default 2GB (set CONFIG_ZRAM_SIZE_OVERRIDE option in defconfig)
<br>  Add exfat
<br>  Skip thermal throttling when charging  (echo 1 > /sys/module/smb5_lib/parameters/skip_thermal)
<br>  Add ntfs
<br>  Add pixel4 cpusets_assist
<br>  Add devfreq_boost
<br>  Add Network File Systems
<br>  Upstream WALT
<br>  Qcom touch_boost
<br>  Add vdso32
<br>  Add some HID driver (include Steam Controller, Nintendo switch Controller and XBox gamepad)
<br>  Add Shadow Call Stack and disabled
<br>  Add qcacld3 wlan driver
<br>  Add andreno boost
<br>  All of them has built in kernel instead of in modules
<br>  Upgrade wireguard Network security tunnel
<br>  Optimize f2fs
<br>  Zram: use lz4 compression and set default
<br>  Enable target TTL
<br>  use power efficient workingqueues
<br>  LLD link and ThinLTO support
<br>  66 69 72 75HZ support
<br>  Compiled based on Qualcomm CAF kernel tree, using the latest driver, more fluent and power saving
<br>  .........
  
## How to install or use it
<br>  First on the premise of removing the mandatory encryption of data partition, back up your existing boot.img and dtbo.img and flash magisk, then swipe the kernel package into twrp and restart it.
<br>  Second enter your system, install kali chroot and reboot.

If you want to use HID,you should run `setprop sys.usb.config win,hid` as root on the terminal.

<br>  Please see [here](https://github.com/kimocoder/qualcomm_android_monitor_mode) to see how to turn wlan0 monitor mode on.

<br>  Due to the special nature of the newly added rtl8812au network card, it is not possible to directly use airmon-ng to directly start the monitoring mode, which can be run by the following command:
<br>  Xiaomi phone need set wlan2 instead of wlan1
<br>  `ip link wlan2 down` 
<br>  `iw dev wlan2 set type monitor`
<br>  `ip link wlan2 up`

## Known Issues
Please tell me

## Thanks (Randomly arranged)
<br> Thanks [CAF-SM8150](https://source.codeaurora.org/quic/la/kernel/msm-4.14/) for kernel tree
<br> Thanks [Android-linux-stable](https://github.com/android-linux-stable/msm-4.14/tree/kernel.lnx.4.14.r4-rel) for kernel source
<br> Thanks [Googlesource](https://android.googlesource.com/kernel/common/+/refs/heads/android-4.14-q) kernel source
<br> Thanks [kimocoder](https://github.com/kimocoder) for rtl88xxau driver and any help 
<br> Thanks [johanlike](https://github.com/johanlike) for Enable Qcom WiFi monitor mode and any help
<br> Thanks [simonpunk](https://forum.xda-developers.com/oneplus-5/development/burgerhunter-t3638810) for HID patch
<br> Thanks [Evirakernel](https://github.com/evirakernel) for some help
<br> Thanks [acai66](https://github.com/acai66) for any help
<br> Thanks [h1jacker](https://github.com/h1jacker) for any help
<br> Thanks [Bcap03](https://github.com/Bcap03) for any help
<br> Thanks [osm0sis](https://github.com/osm0sis/AnyKernel3) for busybox and anykernel3

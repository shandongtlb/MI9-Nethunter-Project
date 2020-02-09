# MI9-Nethunter-Project
Warning: This kernel is intended for hacker technology learning and communication, not for illegal use, all behaviors and responsibilities have nothing to do with me!

This kernel is modified based on Evirakernel and is suitable for MIUI_Q. The kernel version is 4.14.170. It can be updated irregularly later. You can download and use the kernel from release.

## Kernel function
<br>  WIFI Injection (support otg rt3070l ar9170 rtl8187.......)
<br>  HID attack
<br>  SYSVIPC (now you can run postgresql normally)
<br>  USB RNDIS
<br>  RTL-SDR
<br>  USB serial (now it supports ch340 and pl2303)
<br>  Wireless extension compatible (now you can use "iwconfig" and set monitor mode)
<br>  Update to 4.14.170
<br>  Add bbrplus and set default
<br>  Add 830mhz gpu freq
<br>  Add klapse5.0
<br>  Add zen i/o sched and set default
<br>  Add dynamic fsync
<br>  Try ddr 2133
<br>  Add exfat
<br>  Add qcacld3 wlan driver
<br>  .........
  
## How to install
<br>  First back up your existing boot.img and dtbo.img and then swipe the kernel package into twrp and then into magick, and restart it.
<br>  Second enter your system, unzip the kernel package, and extract init.nethunter.rc.disabled, keyboard-descriptor.bin and mouse-descriptor.bin from tool/ppp/,then put the keyboard-descriptor.bin and mouse-descriptor.bin files in the / ;copy all contents in init.nethunter.rc.disabled to the last line of /init.usb.configfs.rc file.
<br>  Finally Install kali chroot and reboot.
If you want to use HID,you should run "setprop sys.usb.config win,hid" as root on the terminal.

## Known Issues
  Please tell me

## Thanks
<br>  [Evirakernel](https://github.com/evirakernel) thanks for kernel source
<br>  [simonpunk](https://forum.xda-developers.com/oneplus-5/development/burgerhunter-t3638810) thanks for HID patch
<br>  [kimocoder](https://github.com/kimocoder) thanks for WIFI injection patch
<br>  [osm0sis](https://github.com/osm0sis/AnyKernel3) thanks for busybox and anykernel3
<br>  [johanlike](https://github.com/johanlike) thanks for any help
<br>  [acai66](https://github.com/acai66) thanks for any help
<br>  [h1jacker](https://github.com/h1jacker) thanks for any help

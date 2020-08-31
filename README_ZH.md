# MI9-Nethunter-Project
<br> 警告：该内核仅在用于黑客技术的学习和交流，禁止非法使用，期间发生和导致的任何责任问题都与本人无关！ [For English](https://github.com/shandongtlb/MI9-Nethunter-Project)

<br> 该内核基于高通官方CAF-SM8150源码合并小米内核树并进行修改，适用于MIUI_Q,基本上实现了Nethunter官网支持手机的全部功能并且已解决所有已知问题
<br> 开源源码地址（并没有打Nethunter补丁，可以自行用我提供的patch合并,当然你还需要自己配置defconfig） [kernel source](https://github.com/shandongtlb/msm-4.14)

<br> Nethunter补丁，理论上支持所有4.14.x内核版本的手机 [Nethunter kernel patch](https://github.com/shandongtlb/MI9-Nethunter-Project/blob/master/MI9-nethunter-4.14.patch)
<br> 小米9 Nethunter内核下载地址 [here](https://github.com/shandongtlb/MI9-Nethunter-Project/releases) 
<br> The last version: V19 20200831 4.14.195 LTS
## 内核功能
### 内核Nethunter功能 (可以使用我提供的补丁来实现 WIFI inject和HID,当然你还需要自己配置defconfig [patch](https://github.com/shandongtlb/MI9-Nethunter-Project/blob/master/MI9-nethunter-4.14.patch))
<br>  WiFi 网卡监听注入 支持2.4GHZ和5GHZ频段
<br>  支持otg外接网卡 MTKMT7601U rt28xx/3070l ar9170 rtl8187/8 ZD1201USB等等
<br>  加入新的RTL88xxAU网卡驱动！具体使用方法请看：https://github.com/aircrack-ng/rtl8812au (我默认未编译，想用的自行编译)
<br>  HID模拟键盘鼠标攻击，完美支持DuckyHID
<br>  SYSVIPC支持 (现在你可以开启PostgreSQL数据库)
<br>  DriveDroid支持
<br>  USB RNDIS 模拟网卡
<br>  USB/UART 蓝牙设备支持
<br>  RTL-SDR, AirSpy, Hackrf 支持
<br>  USB RTL8150/2/3 based 有线网卡支持
<br>  USB serial (目前支持CH341和pl2303接口)
<br>  无线扩展兼容性 (现在你可以通过使用`iwconfig`命令开启监听模式)
<br>  支持高通内置网卡开启监听, 现在你可以使用手机自身的"wlan0"网卡来开启监听模式了(暂不支持注入)
### 内核自身功能
<br>  Update to 4.14.195
<br>  Merge tag 'LA.UM.8.1.r1-15800-sm8150.0' for kernel tree, WLAN, Audio, data_rmnet
<br>  合并谷歌最新common android-4.14-q
<br>  添加 BBRv2 and set default
<br>  添加 810mhz gpu freq
<br>  添加 klapse5.0
<br>  添加 Audio control
<br>  添加 zen i/o调度器并设为默认
<br>  添加 dynamic fsync 并且默认关闭
<br>  设置 ddr 2133MHZ
<br>  合并上游 simple LMK
<br>  添加 cpu input boost
<br>  优化 EAS 能量模型
<br>  使用 WALT
<br>  电池充电容量解锁
<br>  使用pixel4的cpusets_assist，相同任务效率更高(在此感谢流念帖子给的思路)
<br>  跳过充电温控，默认关闭 开启：echo 1 > /sys/module/smb5_lib/parameters/skip_thermal
<br>  强制 USB MTP 模式 900ma 快充，默认开启
<br>  设置 zram 默认2GB （可以在defconfig调节 CONFIG_ZRAM_SIZE_OVERRIDE 这个参数修改）
<br>  添加 exfat
<br>  添加 ntfs
<br>  添加 devfreq_boost
<br>  添加 Network File Systems
<br>  添加 vdso32
<br>  添加一些HID驱动 (包括 Steam Controller, Nintendo switch Controller 和 XBox 游戏手柄)
<br>  添加 Shadow Call Stack(SCS) 并且默认关闭
<br>  升级 qcacld3 wlan driver 到最新
<br>  添加 andreno boost 并且默认关闭
<br>  高通触摸升频
<br>  实现 0 模块，将所有东西都编译进内核，增强通刷性
<br>  升级 wireguard 到最新
<br>  优化 f2fs
<br>  Zram: 默认lz4压缩算法
<br>  开启 target TTL 接口
<br>  use power efficient workingqueues
<br>  LLD link and ThinLTO support
<br>  支持屏幕刷新率 66 69 72 75hz
<br>  使用基于高通的CAF编译，最新的驱动，更流畅更省电
<br>  还有很多很多不一一列举了哈.........
  
## 如何安装和使用
<br>  第一步首先在已经去除data分区强制加密的前提下在twrp备份你的boot.img和dtbo.img，然后刷入面具，最后刷入内核包，重启
<br>  第二步进入到你的系统，安装chroot并重启系统
<br>  如果你想开启HID，你需要到终端模拟器以root身份键入以下命令 `setprop sys.usb.config win,hid`

<br>  如果你想开启手机内置网卡wlan0的监听功能, [请看这里](https://github.com/kimocoder/qualcomm_android_monitor_mode) 

<br>  由于新增rtl8812au网卡的特殊性无法直接用airmon-ng直接开启监听模式，可以通过下列命令运行:
<br>  小米手机的话要操作的应该使wlan2而不是wlan1
<br>  `ip link wlan2 down`
<br>  `iw dev wlan2 set type monitor`
<br>  `ip link wlan2 up`

<br>  建议各位使用官改MIUI12，指纹问题已经解决，在此向流念、len以及sk大佬表以感谢和致敬！！！

## 已知问题
请告诉我哦

## 感谢名单 (排名不分先后)
<br> Thanks [CAF-SM8150](https://source.codeaurora.org/quic/la/kernel/msm-4.14/) for kernel source
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

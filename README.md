# meta-rinato
Attempt at porting AsteroidOS to Rinato/Gear 2 & Gear 2 Neo

Currently doesn't even have anything

## useful stuff
https://patchwork.kernel.org/project/linux-arm-kernel/patch/1415360662-30390-1-git-send-email-k.kozlowski@samsung.com/ - Patch to add retail Gear2 to compatible devices

https://github.com/openembedded/openembedded-core/blob/master/meta/conf/machine/qemuarm.conf - qemu arm config for openembedded

`console=ram loglevel=4 no_console_suspend androidboot.selinux=disabled root=/dev/mmcblk0p8 rw rootfstype=ext4 rootwait sec_debug.enable=0 sec_debug.enable_user=0 sec_watchdog.sec_pet=5 sec_log=0x200000@0x46000000 androidboot.serialno=redacted tizenboot.emmc_checksum=3 tizenboot.odin=1 bootloader.ver=R380XXU0BOA2 bootloader.fb=0x48000000 bootloader.log=0x15d5@0x4603ceef` - Android wear port's cmdline

`console=ram loglevel=4 root=/dev/mmcblk0p15 ro rootfstype=ext4 rootwait bootmode=normal pwron.reason=ap:swrst,pmic:acok sec_debug.enable=0 sec_debug.enable_user=0 sec_watchdog.sec_pet=5 sec_log=0x200000@0x46000000 lcdtype=0 oops=panic pmic_info=1875 sysscope=0xee000000 cordon=310baa3d7e5cd27155b0d44028aebdfd serialno=redacted tizenboot.emmc_checksum=3 tizenboot.odin=1 bootloader.ver=R380XXU0BOA2 bootloader.fb=0x48000000 bootloader.log=0x157d@0x46028ee5` - Tizen's cmdline from plusmid

Partition Layout - https://forum.xda-developers.com/t/porting-android-to-gear-2.2992953/

```bota0 -> ../../mmcblk0p1
bota1 -> ../../mmcblk0p2
csa -> ../../mmcblk0p3 --> ext4 -> /csa
boot -> ../../mmcblk0p5 --> Main Kernel
csc -> ../../mmcblk0p12 --> ext4 -> /system/csc
fota -> ../../mmcblk0p10 --> seems empty
ramdisk-recovery -> mmcblk0p8 -> ext4 -> Unused in tizen --> USED AS BOOT PARTITION IN ANDROID
module -> ../../mmcblk0p9 --> ext4 -> /lib/modules --> USED FOR TWRP IN ANDROID
rootfs -> ../../mmcblk0p15 ext4 "/" --> Root file system, recovery works from here too. If you break it it will only boot to download mode. --> USED AS SYSTEM PARTITION IN ANDROID
system -> ../../mmcblk0p11 EMPTY --> Did samsung start with Android on this thing then changed their minds?
system-data -> ../../mmcblk0p13 --> ext4, /opt --> If you erase this partition, your watch won't boot back into Tizen. Do not touch it unless you have a backup and know your way into restoring it.
user -> ../../mmcblk0p14 EXT4, /opt/usr --> all user data, including the MTP available part (/opt/usr/media) --> USED AS DATA & SDCARD IN ANDROID
```
## links
https://exynos.wiki.kernel.org/start

https://forum.xda-developers.com/t/porting-android-to-gear-2.2992953/

https://wiki.postmarketos.org/wiki/Samsung_Gear_2_(samsung-rinato)

https://libera.irclog.whitequark.org/linux-exynos/2021-06-28

https://github.com/AsteroidOS/asteroid/issues/127

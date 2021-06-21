# meta-rinato
Attempt at porting AsteroidOS to Rinato/Gear 2 & Gear 2 Neo

Currently doesn't even have anything

## useful stuff
https://patchwork.kernel.org/project/linux-arm-kernel/patch/1415360662-30390-1-git-send-email-k.kozlowski@samsung.com/ - Patch to add retail Gear2 to compatible devices

https://github.com/openembedded/openembedded-core/blob/master/meta/conf/machine/qemuarm.conf - qemu arm config for openembedded

`console=ram loglevel=4 no_console_suspend androidboot.selinux=disabled root=/dev/mmcblk0p8 rw rootfstype=ext4 rootwait sec_debug.enable=0 sec_debug.enable_user=0 sec_watchdog.sec_pet=5 sec_log=0x200000@0x46000000 androidboot.serialno=4100ed5b430331a3 tizenboot.emmc_checksum=3 tizenboot.odin=1 bootloader.ver=R380XXU0BOA2 bootloader.fb=0x48000000 bootloader.log=0x15d5@0x4603ceef` - Android wear port's cmdline

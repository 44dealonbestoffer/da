The [Genode OS Framework](http://genode.org/index) supports the USB armory since version [15.02](http://genode.org/documentation/release-notes/15.02#Support_for_the_USB-Armory_board) implementing a TrustZone Secure [virtual-machine monitor](http://genode.org/documentation/articles/trustzone) (VMM) supervising Linux running in the Normal world.

Support is in the very early stages, the following notes provides some hint to get started.

The Linux kernel requires minimal patching to be executed in the Normal world, at the moment Martin Stein from Genode Labs provides a [repository](https://github.com/m-stein/linux/tree/usb_armory_genode_tz_vmm) with a patched kernel.

The image must be compiled with the following load address:

```
make ARCH=arm zImage LOADADDR=0x80008000 modules
```

The Genode OS image, embedding a sample Linux kernel with initrd image, can be compiled as follows:

```
git clone https://github.com/genodelabs/genode
cd genode
./tool/create_builddir hw_usb_armory
cd build/hw_usb_armory
# in etc/build.conf add "--include image/uboot" to RUN_OPT
make run/tz_vmm
cp var/run/tz_vmm/uImage $SD_CARD_MNT
# boot USB armory with SD card and stop Uboot countdown (requires serial connection)
uboot> ext2load mmc 0:1 0x70200000 /boot/uImage-genode; bootm 0x70200000
```
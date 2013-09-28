# Linux boot wrapper with FDT support

A fork of
git://git.kernel.org/pub/scm/linux/kernel/git/cmarinas/boot-wrapper-aarch64.git

Core contents:
- model.lds.S
- boot.S
- Makefile

Build your kernel (using
[this](https://aur.archlinux.org/packages/gcc-aarch64-linaro-gnu)
cross-compiler toolchain) and symlink the following files:

- Image: symlink to <linuxroot>/arch/arm64/boot/Image

- dtc: symlink to to <linuxroot>/scripts/dtc/dtc

- foundation-v8.dts: symlink to
  <linuxroot>/arch/arm64/boot/dts/foundation-v8.dts

- Foundation_v8 and libarmctlmodel.so are part of the ARM foundation
  model, which can be downloaded from the website: [ARM
  website](https://silver.arm.com/browse/FM00A)

- raring-arm64-rootfs is available from
  http://people.debian.org/~wookey/bootstrap/rootfs/

Once the make target linux-system.axf is built from the kernel image,
run the emulator like:

    $ ./Foundation_v8 --image linux-system.axf --cores 4 --block-device raring-arm64-rootfs

Notice the kernel parameter `root=/dev/vda` in the Makefile: the
raring-arm64-rootfs supplied on command-line is exposed as a virtio
block device.

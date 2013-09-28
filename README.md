# Linux boot wrapper with FDT support

The following files need to be linked into the boot wrapper directory:

- dtc: symlink to to <linux-build-dir>/scripts/dtc/dtc
- foundation-v8.dts: symlink to <linux-src-dir>/arch/arm64/boot/dts/foundation-v8.dts

Alternatively, you may specify the paths for dtc and the main dts file
on the make command-line. For example:

make DTC=<path-to-dtc> FDT_SRC=<linux-src-dir>/arch/arm64/boot/dts/vexpress-v2p-aarch64.dtsi

raring-arm64-rootfs is available from http://people.debian.org/~wookey/bootstrap/rootfs/

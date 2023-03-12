# Buildroot_Kernel_5.15_bug
applying a JTAG patch multiple time that leads to Error

```
>>> linux-headers 5.15.91 Patching
for p in board/beaglebone/patches/linux ; do if test -d $p ; then PATH=/home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/output/host/bin:$PATH support/scripts/apply-patches.sh  /home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/output/build/linux-headers-5.15.91 $p \*.patch || exit 1 ; else PATH=/home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/output/host/bin:$PATH support/scripts/apply-patches.sh  /home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/output/build/linux-headers-5.15.91 `dirname $p` `basename $p` || exit 1; fi done

Applying 0001-keep-jtag-clock-alive-for-debugger.patch using patch: 
Error: duplicate filename '0001-keep-jtag-clock-alive-for-debugger.patch'
Conflicting files are:
  already applied: /home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/board/beaglebone/patches/linux/0001-keep-jtag-clock-alive-for-debugger.patch
  to be applied  : /home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/board/beaglebone/patches/linux/0001-keep-jtag-clock-alive-for-debugger.patch
package/pkg-generic.mk:247: recipe for target '/home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/output/build/linux-headers-5.15.91/.stamp_patched' failed
make[1]: *** [/home/ali/Documents/SEMI_BBB/buildroot/buildroot-2022.02.10/output/build/linux-headers-5.15.91/.stamp_patched] Error 1
Makefile:84: recipe for target '_all' failed
make: *** [_all] Error 2
```

## Solution :

Just Remove the file from that path and then run the "make" command again, FIXED !!

You can put the patch file back in its place after build process finished :)

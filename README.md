yavta
====

Yet Another V4L2 Test Application

To compile
----
>root@local: ~/source/yavta# CROSS_COMPILE=aarch64-linux-gnu- make
>
>_OR_
>
>root@local: ~/source/yavta# meson setup --cross-file cross.txt build
>
>root@local: ~/source/yavta# meson compile -C build
>
>>root@local: ~/source/yavta# file yavta
>
>yavta: ELF 64-bit LSB executable, ARM aarch64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=87269762875bec0712202e689992b1d1c721edf1, for GNU/Linux 3.7.0, not stripped

# tinker-kdev
Tinkerboard kernel with acceleration support, compiled -Ofast

Source for build environment:
'''
git clone https://github.com/armbian/build
'''
Source for binary blobs and includes to use them:
'''
https://github.com/rockchip-linux/libmali
'''
Source to use kmsdrm on the mali GPU:
'''
https://github.com/rockchip-linux/libdrm-rockchip
'''
You only need the lib and include directories.
Copy them to /usr/local.

This repository contains:
1) A copy of the kconfig used to make the 4.14.14 kernel capable of acceleration on the tinkerboard.  For the full source, consult my source listed above (the build environment).  The kernel supports up to libMali ABI 14.
2) A mirror of the libmali blobs also available at the second link above.  It also includes an install script that will get the appropriate symlinks and includes into /usr/local.
3) A copy of my custom Tinkerboard device-tree blob and source.  It is capable of 1.92ghz (I found 2ghz to be unstable.)

Please use these to replicate the kernel in your own environments.  The kconfig file should work for new kernel versions, and the same for the device tree sources. 

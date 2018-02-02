# tinker-kdev
Tinkerboard kernel with acceleration support, compiled -Ofast

Source for build environment:
* git clone https://github.com/armbian/build

Source for binary blobs and includes to use them:
* https://github.com/rockchip-linux/libmali
* You only need the lib and include directories.  Copy them to /usr/local.

Source to use kmsdrm on the mali GPU:
* https://github.com/rockchip-linux/libdrm-rockchip


This repository contains:
1) A copy of the kconfig used to make the 4.14.14 kernel capable of acceleration on the tinkerboard.  For the full source, consult my source listed above (the build environment).  The kernel supports up to libMali ABI 14.
2) A mirror of the libmali blobs also available at the second link above.  It also includes an install script that will get the appropriate symlinks and includes into /usr/local.  The drivers support libMali ABI 12.
3) A copy of my custom Tinkerboard device-tree blob and source.  It is capable of 1.92ghz (I found 2ghz to be unstable.)

Please use these to replicate the kernel in your own environments.  The kconfig file should work for new kernel versions, and the same for the device tree source. 

This kernel config and blobs have been tested on Armbian (debian-jessie-next) and DietPi (debian-stretch) and verified to work.

Some notes:
I have noticed that the libmali blobs all seem to have the same function calls but init the display a different way, so you want libmali*-gbm to replace libgbm.so, libmali*-wayland for wayland, and so on.  You can link directly against one of them for your application.   I particularly recommend installing libgbm-dev, compiling the libdrm-rockchip above, and then linking things against libmali*-gbm.so, if your application supports kms-drm, as it seems to be the fastest and most modern solution.  This works particularly well with SDL2 (the -fbdev version works best with SDL1).  However libraries for utilizing acceleration with wayland, x11-fbdev, plain fbdev, and kms-drm via gbm are provided.

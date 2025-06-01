# EmbeddedLinuxBBB ;

------------------------------------------------------------------------------

Step 1:
cp PROJECT-BBB/pre-built-images/* /Workspace-BBB/BOOT.
Step 2:
minicom -b 115200 -o -D /dev/ttyACM0
Step 3:
Partition SD Card as BOOT fat16 with boot flag and ROOTFS ext3.
Step 4:
cd /Workspace-BBB/BOOT; 
sudo cp BBB_MLO /media/ranganadh/BOOT/MLO
Step 5:
sudo cp u-boot.img /media/ranganadh/BOOT/u-boot.img
Step 6:
cd /Workspace-BBB/ROOTFS; 
sudo cp -r * /media/ranganadh/ROOTFS/; sync;
sudo cp uImage /media/ranganadh/ROOTFS/boot/uImage
sudo cp am335x-boneblack.dtb /media/ranganadh/ROOTFS/boot/am335x-boneblack.dtb
Step 7:
cd /Workspace-BBB/BOOT; 
sudo cp uEnv.txt /media/ranganadh/BOOT/uEnv.txt

------------------------------------------------------------------------------

Step 1:
https://docs.u-boot.org/en/latest/build/source.html
Step 2:
git clone https://github.com/u-boot/u-boot;
git clone https://github.com/eewiki/u-boot-patches.git;
cp u-boot-patches/v2019.04/0001-am335x_evm-uEnv.txt-bootz-n-fixes.patch ../../u-boot/;
cp u-boot-patches/v2019.04/0002-U-Boot-BeagleBone-Cape-Manager.patch ../../u-boot/;
cd ../../u-boot;
patch -p1 < 0001-am335x_evm-uEnv.txt-bootz-n-fixes.patch;
patch -p1 < 0002-U-Boot-BeagleBone-Cape-Manager.patch;
Step 3:
sudo apt-get install gcc gcc-aarch64-linux-gnu
sudo apt-get install gcc-arm*
Step 4:
sudo apt-get install bc bison build-essential coccinelle \
  device-tree-compiler dfu-util efitools flex gdisk graphviz imagemagick \
  libgnutls28-dev libguestfs-tools libncurses-dev \
  libpython3-dev libsdl2-dev libssl-dev lz4 lzma lzma-alone openssl \
  pkg-config python3 python3-asteval python3-coverage python3-filelock \
  python3-pkg-resources python3-pycryptodome python3-pyelftools \
  python3-pytest python3-pytest-xdist python3-sphinxcontrib.apidoc \
  python3-sphinx-rtd-theme python3-subunit python3-testtools \
  python3-venv swig uuid-dev
Step 5:
export ARCH=arm 
export CROSS_COMPILE=arm-linux-gnueabihf-
make distclean
make am335x_evm_defconfig
make DEVICE_TREE=am335x-boneblack
Step 6:
make menuconfig
make
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j10

------------------------------------------------------------------------------

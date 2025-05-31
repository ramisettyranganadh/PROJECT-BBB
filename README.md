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

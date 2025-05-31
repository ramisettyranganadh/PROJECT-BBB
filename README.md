# EmbeddedLinuxBBB ;
Step 1: (Secondary Program Loader or Memory/MMC LOader)
copy images from PROJECT-BBB/pre-built-images/ and paste in Local Workspace.
Step 2:
Run minicom -b 115200 -o -D /dev/ttyACM0 and Power Up the Beagle Bone Black.
Step 3:
Partition SD Card into BOOT fat16 with boot flag and ROOTFS ext3.
Step 4: (rename as MLO)
cd /home/ranganadh/Embedded/Workspace-BBB/BOOT; sudo cp MLO /media/ranganadh/BOOT/

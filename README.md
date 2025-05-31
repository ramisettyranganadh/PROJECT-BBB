# EmbeddedLinuxBBB ;
Step 1: (Secondary Program Loader or Memory/MMC LOader)
copy images from PROJECT-BBB/pre-built-images/ and paste in Local Workspace.
Step 2: (UART)
Run minicom -b 115200 -o -D /dev/ttyACM0 and Power Up the Beagle Bone Black.
Step 3: (SD Card)
Partition SD Card into BOOT fat16 with boot flag and ROOTFS ext3.
Step 4: (rename as MLO and copy to SD Card BOOT)
cd /Workspace-BBB/BOOT; sudo cp MLO /media/ranganadh/BOOT/

# EmbeddedLinuxBBB ;

https://github.com/niekiran/EmbeddedLinuxBBB/tree/master/pre-built-images/serial-boot

----------------------Debug Probe Serial Communication---------------------

    minicom -b 115200 -o -D /dev/ttyACM0
    Press any Key within 3 Seconds to U-BOOT
    printenv; env set ranganadh ramisetty; printenv ranganadh;

---------------------------Load Images from UART---------------------------

    Press S2 and Power ON, Press Ctrl A + S and select Xmodem then select u-boot-spl.bin, u-boot.img
    Press space and Enter to select and transfer a file over Serial Xmodem
    Enter UBOOT -> loadx 0x82000000 -> Press Ctrl A + S then select uImage
    Enter UBOOT -> loadx 0x88000000 -> Press Ctrl A + S then select dtb
    Enter UBOOT -> loadx 0x88080000 -> Press Ctrl A + S then select initramfs
    Enter UBOOT -> setenv bootargs console=ttyO0,115200 root=/dev/ram0 rw initrd=0x88080000
    Enter UBOOT -> bootm 0x82000000 0x88080000 0x88000000

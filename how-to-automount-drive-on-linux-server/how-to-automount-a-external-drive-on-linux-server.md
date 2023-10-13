We can configure the USB drive so that it can be auto-mounted when plugged in.

1. Insert the external USB drive to the linux server

2. UUID (universal unique identifier) is used in Linux for the detection of the USB which is plugged in or for the identification of the partition used by the USB drive. Because of this we have to be a root user. We can be a root user by the **sudo** command, it will ask for a password.

3. Use this command to list the disk or dirves connected
```
pi@raspberrypi:~ $ lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda           8:0    1   30G  0 disk 
└─sda1        8:1    1   30G  0 part /home/pi/pd
mmcblk0     179:0    0  7.4G  0 disk 
├─mmcblk0p1 179:1    0  256M  0 part /boot
└─mmcblk0p2 179:2    0  7.1G  0 part /

```
4. In this case, I want to use the sda1 drive to be automounted, for mounting the drive we need to create a folder in the main file structure 

```
pi@raspberrypi:/home $ cd ../
pi@raspberrypi:/ $ ls
bin  boot  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
pi@raspberrypi:/ $ cd media
pi@raspberrypi:/media $ ls
externaldrive
```

```
sudo mkdir extdrive
```
> /media/externaldrive


or simply we can create a folder in the home directory to make it more easy for access

```
sudo mkdir extdrive
```

5. To find the UUID of the drive connected use the command

> blkid

```
pi@raspberrypi:/media $ blkid
/dev/mmcblk0p1: LABEL_FATBOOT="boot" LABEL="boot" UUID="37E2-62C3" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="1260ca97-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="6a932c1f-7335-42d9-9351-1b1b2ca538d4" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="1260ca97-02"
/dev/sda1: BLOCK_SIZE="512" UUID="3586E91701E285AD" TYPE="ntfs" PARTUUID="30b23504-01"
```

6. Now once, we get the UUID copy it and update it in the fstab file using the command

```
sudo nano /etc/fastab
```

```
proc            /proc           proc    defaults          0       0
PARTUUID=1260ca97-01  /boot           vfat    defaults,flush    0       2
PARTUUID=1260ca97-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that


#for pendrive automount
UUID=3586E91701E285AD   /home/pi/extdrive     ntfs    defaults 0 0
```

save the file in nano using Ctrl+x and y to save it.

7. Mount the drive using

```
sudo mount -t ntfs-3g /dev/sda1 /home/pi/extdrive
```

That's it reboot the system!!!

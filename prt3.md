```
root@yangqi:~# lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0 70.4M  1 loop /snap/lxd/19647
loop1                       7:1    0 55.4M  1 loop /snap/core18/1944
loop2                       7:2    0 32.3M  1 loop /snap/snapd/11107
loop3                       7:3    0 55.5M  1 loop /snap/core18/1988
loop4                       7:4    0 32.3M  1 loop /snap/snapd/11402
loop5                       7:5    0 69.9M  1 loop /snap/lxd/19188
sda                         8:0    0   10G  0 disk 
vda                       252:0    0   20G  0 disk 
├─vda1                    252:1    0    1M  0 part 
├─vda2                    252:2    0    1G  0 part /boot
└─vda3                    252:3    0   19G  0 part 
  └─ubuntu--vg-ubuntu--lv 253:0    0   19G  0 lvm  /
root@yangqi:~# fdisk /dev/sda

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x2c901af1.

Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): e
Partition number (1-4, default 1): 
First sector (2048-20971519, default 2048): 
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-20971519, default 20971519): 8388608

Created a new partition 1 of type 'Extended' and of size 4 GiB.

Command (m for help): p
Disk /dev/sda: 10 GiB, 10737418240 bytes, 20971520 sectors
Disk model: QEMU HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2c901af1

Device     Boot Start     End Sectors Size Id Type
/dev/sda1        2048 8388608 8386561   4G  5 Extended

Command (m for help): w

The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.

root@yangqi:~# lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0 70.4M  1 loop /snap/lxd/19647
loop1                       7:1    0 55.4M  1 loop /snap/core18/1944
loop2                       7:2    0 32.3M  1 loop /snap/snapd/11107
loop3                       7:3    0 55.5M  1 loop /snap/core18/1988
loop4                       7:4    0 32.3M  1 loop /snap/snapd/11402
loop5                       7:5    0 69.9M  1 loop /snap/lxd/19188
sda                         8:0    0   10G  0 disk 
└─sda1                      8:1    0    4G  0 part 
vda                       252:0    0   20G  0 disk 
├─vda1                    252:1    0    1M  0 part 
├─vda2                    252:2    0    1G  0 part /boot
└─vda3                    252:3    0   19G  0 part 
  └─ubuntu--vg-ubuntu--lv 253:0    0   19G  0 lvm  /
```
```
root@yangqi:~# mkfs.xfs -f /dev/sda1
meta-data=/dev/sda1              isize=512    agcount=4, agsize=262080 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=1, sparse=1, rmapbt=0
         =                       reflink=1
data     =                       bsize=4096   blocks=1048320, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0, ftype=1
log      =internal log           bsize=4096   blocks=2560, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
root@yangqi:/data1# mount /dev/sda1 /data1
root@yangqi:/data1# mount /dev/sda1 /data1
mount: /data1: /dev/sda1 already mounted on /data1.
root@yangqi:/data1# 
```

```

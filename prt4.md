```
sda                         8:0    0   10G  0 disk 
├─sda1                      8:1    0    4G  0 part /data1
├─sda2                      8:2    0    2G  0 part 
└─sda3                      8:3    0    2G  0 part 
vda                       252:0    0   20G  0 disk 
├─vda1                    252:1    0    1M  0 part 
├─vda2                    252:2    0    1G  0 part /boot
└─vda3                    252:3    0   19G  0 part 
  └─ubuntu--vg-ubuntu--lv 253:0    0   19G  0 lvm  /
root@yangqi:/data1# pvs
  PV         VG        Fmt  Attr PSize   PFree
  /dev/sda2            lvm2 ---    2.00g 2.00g
  /dev/sda3            lvm2 ---    2.00g 2.00g
  /dev/vda3  ubuntu-vg lvm2 a--  <19.00g    0 
root@yangqi:/data1# vgcreate testvg /dev/sda2 /dev/sda3
  Volume group "testvg" successfully created
root@yangqi:/data1# vgs
  VG        #PV #LV #SN Attr   VSize   VFree
  testvg      2   0   0 wz--n-   3.99g 3.99g
  ubuntu-vg   1   1   0 wz--n- <19.00g    0 
root@yangqi:/data1# 
```
```
└─sda4                      8:4    0    1G  0 part 
vda                       252:0    0   20G  0 disk 
├─vda1                    252:1    0    1M  0 part 
├─vda2                    252:2    0    1G  0 part /boot
└─vda3                    252:3    0   19G  0 part 
  └─ubuntu--vg-ubuntu--lv 253:0    0   19G  0 lvm  /
root@yangqi:/data1# vgextend testvg /dev/sda4
  Physical volume "/dev/sda4" successfully created.
  Volume group "testvg" successfully extended
root@yangqi:/data1# 
```

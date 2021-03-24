```
root@yangqi:/# find -name shadow
./snap/core18/1988/etc/shadow
./snap/core18/1988/var/lib/extrausers/shadow
./snap/core18/1944/etc/shadow
./snap/core18/1944/var/lib/extrausers/shadow
./etc/shadow
root@yangqi:/# 
```
```
root@yangqi:/# mkdir /opt/nginx1.8.5
root@yangqi:/# ln -s /opt/nginx1.8.5 /nginx
root@yangqi:/# ls -l nginx
lrwxrwxrwx 1 root root 15 Mar 24 01:24 nginx -> /opt/nginx1.8.5
root@yangqi:/# ls -l opt
total 12
drwxr-xr-x 3 root root 4096 Mar 24 00:52 aaa
drwxr-xr-x 3 root root 4096 Mar 24 00:49 data1
drwxr-xr-x 2 root root 4096 Mar 24 01:25 nginx1.8.5
-rw-r--r-- 1 root root    0 Mar 24 00:57 test3
root@yangqi:/# 
```
```
root@yangqi:/# mkdir opt/abc
root@yangqi:/# useradd abc
root@yangqi:~# chown abc /opt/abc
```
```
root@yangqi:~# mkdir /opt/testabc
root@yangqi:~# groupadd testabc
root@yangqi:~# chown :testabc /opt/testabc
root@yangqi:/opt# stat testabc
  File: testabc
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: fd00h/64768d	Inode: 791408      Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: ( 1002/ testabc)
Access: 2021-03-24 01:33:56.232986369 +0000
Modify: 2021-03-24 01:33:56.232986369 +0000
Change: 2021-03-24 01:35:40.510185060 +0000
```

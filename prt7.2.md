```
root@yangqi:~# ss -tap | grep mysql
LISTEN   0        70               127.0.0.1:33060              0.0.0.0:*        users:(("mysqld",pid=10327,fd=32))                                             
LISTEN   0        151              127.0.0.1:mysql              0.0.0.0:*        users:(("mysqld",pid=10327,fd=34))                                             
root@yangqi:~# 
```

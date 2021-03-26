```
root@yangqi:~# ss -tap | grep mysql
LISTEN   0        70               127.0.0.1:33060              0.0.0.0:*        users:(("mysqld",pid=10327,fd=32))                                             
LISTEN   0        151              127.0.0.1:mysql              0.0.0.0:*        users:(("mysqld",pid=10327,fd=34))                                             
root@yangqi:~# 
```
```
root@yangqi:~# php -v
PHP 7.4.3 (cli) (built: Oct  6 2020 15:47:56) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Zend OPcache v7.4.3, Copyright (c), by Zend Technologies
root@yangqi:~# php main.php
PHP is best
-+-+-+-+-+-
root@yangqi:~# 
```

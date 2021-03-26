```shell
root@yangqi:~# mysql --version
mysql  Ver 8.0.23-0ubuntu0.20.04.1 for Linux on x86_64 ((Ubuntu))
root@yangqi:~# systemctl enable mysql.service
Synchronizing state of mysql.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mysql
Created symlink /etc/systemd/system/multi-user.target.wants/mysql.service → /lib/systemd/system/mysql.service.
root@yangqi:~# 
```
```
root@yangqi:~# mysql -u root -p mysql
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 12
Server version: 8.0.23-0ubuntu0.20.04.1 (Ubuntu)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
mysql> CREATE USER 'yangqi'@'127.0.0.1' IDENTIFIED BY 'passyangqi';
Query OK, 0 rows affected (0.09 sec)

mysql> GRANT SELECT, SHOW VIEW ON *.* TO 'yangqi'@'127.0.0.1';
Query OK, 0 rows affected (0.02 sec)

mysql> 
root@yangqi:~# mysql -u yangqi -p -h 127.0.0.1
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 29
Server version: 8.0.23-0ubuntu0.20.04.1 (Ubuntu)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.01 sec)

mysql> create database TES;
ERROR 1044 (42000): Access denied for user 'yangqi'@'127.0.0.1' to database 'TES'
mysql> 

```
```
```
```
root@yangqi:~# wget https://nginx.org/keys/nginx_signing.key
--2021-03-26 00:51:53--  https://nginx.org/keys/nginx_signing.key
Resolving nginx.org (nginx.org)... 3.125.197.172, 52.58.199.22, 2a05:d014:edb:5704::6, ...
Connecting to nginx.org (nginx.org)|3.125.197.172|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1561 (1.5K) [application/octet-stream]
Saving to: ‘nginx_signing.key’

nginx_signing.key       100%[============================>]   1.52K  --.-KB/s    in 0s      

2021-03-26 00:51:55 (352 MB/s) - ‘nginx_signing.key’ saved [1561/1561]

root@yangqi:~# apt-key add nginx_signing.key
OK
root@yangqi:~# vim /etc/apt/sources.list
deb https://nginx.org/packages/mainline/ubuntu/ focal nginx
deb-src https://nginx.org/packages/mainline/ubuntu/ focal nginx
-- INSERT --                                                               52,64         Bot
root@yangqi:~# nginx
root@yangqi:~# curl -I 127.0.0.1
HTTP/1.1 200 OK
Server: nginx/1.19.8
Date: Fri, 26 Mar 2021 01:18:57 GMT
Content-Type: text/html
Content-Length: 612
Last-Modified: Tue, 09 Mar 2021 15:27:51 GMT
Connection: keep-alive

    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/*.conf;
}
~                                                                                            
~ 
root@yangqi:/etc/nginx# vim *\.conf

```

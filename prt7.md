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
root@yangqi:/etc/nginx/# vim *\.conf
    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/host*.conf;
}
~                                                                                            
~ 
root@yangqi:/etc/nginx/conf.d/host# vim test.conf
server {
    listen       80;
    server_name  yangqi.org;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        root   /var/org/nginx/test/html;
        index  index.html index.htm;
        }
root@yangqi:/etc/nginx/conf.d/host# curl yangqi.org
It's works
root@yangqi:/etc/nginx/conf.d/host# 
```
```
server {
    listen       80;
    server_name  yangqi.org;

    #charset koi8-r;
    access_log  /tmp/yangqi.log  main;

    location / {
root@yangqi:/etc/nginx/conf.d/host# curl yangqi.org
It's works
root@yangqi:/etc/nginx/conf.d/host# 
root@yangqi:/etc/nginx/conf.d/host# ll /tmp
total 52
drwxrwxrwt 12 root root 4096 Mar 26 02:06 ./
drwxr-xr-x 21 root root 4096 Mar 24 02:56 ../
drwxrwxrwt  2 root root 4096 Mar 26 00:08 .font-unix/
drwxrwxrwt  2 root root 4096 Mar 26 00:08 .ICE-unix/
drwx------  3 root root 4096 Mar 26 00:08 snap.lxd/
drwx------  3 root root 4096 Mar 26 00:08 systemd-private-6586f307
drwx------  3 root root 4096 Mar 26 00:08 systemd-private-6586f307
drwx------  3 root root 4096 Mar 26 00:08 systemd-private-6586f307
drwxrwxrwt  2 root root 4096 Mar 26 00:08 .Test-unix/
drwx------  2 root root 4096 Mar 26 01:43 tmux-0/
drwxrwxrwt  2 root root 4096 Mar 26 00:08 .X11-unix/
drwxrwxrwt  2 root root 4096 Mar 26 00:08 .XIM-unix/
-rw-r--r--  1 root root  190 Mar 26 02:08 yangqi.log
root@yangqi:/etc/nginx/conf.d/host# 
```

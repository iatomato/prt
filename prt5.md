```
ryan@yangqi:~$ sudo groupadd mysql
ryan@yangqi:~$ sudo useradd -M -s /sbin/nologin mysql -g mysql
ryan@yangqi:~$ sudo systemctl enable mysqld
ryan@yangqi:~$ sudo systemctl start mysqld
ryan@yangqi:~$ tar zxf mysql-5.6.36.tar.gz -C /usr/src
ryan@yangqi:~$ sduo cd /usr/src/mysql-5.6.36/
ryan@yangqi:~$ sudo cmake \
 -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
 -DSYSCONFDIR=/etc/ -DDEFAULT_CHARSET=utf8 \
 -DDEFAULT_COLLATION=utf8_general_ci \
 -DWITH_EXTRA_CHARSETS=all
ryan@yangqi:~$ sudo make && make install
ryan@yangqi:~$ sudo chown -R mysql:mysql /usr/local/mysql
```
```
`apache2 install`

ryan@yangqi:~/httpd-2.4.46$ tar -xzvf httpd-2.4.46.tar.gz
ryan@yangqi:~/httpd-2.4.46$ sudo apt install libapr1*
ryan@yangqi:~/httpd-2.4.46$ sudo apt install libaprutil1*
ryan@yangqi:~/httpd-2.4.46$ sudo apt install libpcre3-dev
ryan@yangqi:~/httpd-2.4.46$ ./configure --prefix=/usr/local/apache2
ryan@yangqi:~/httpd-2.4.46$ make -j4
ryan@yangqi:~/httpd-2.4.46$ sudo make install
Making install in srclib
make[1]: Entering directory '/home/ryan/httpd-2.4.46/srclib'
make[2]: Entering directory '/home/ryan/httpd-2.4.46/srclib'
make[2]: Leaving directory '/home/ryan/httpd-2.4.46/srclib'

ryan@yangqi:/usr/local/apache2/bin$ ls -l
total 1340
-rwxr-xr-x 1 root root  59728 Mar 25 00:54 ab
-rwxr-xr-x 1 ryan ryan   3437 Mar 25 00:52 apachectl
-rwxr-xr-x 1 ryan ryan  23879 Mar 25 00:52 apxs
-rwxr-xr-x 1 root root  16976 Mar 25 00:54 checkgid
-rwxr-xr-x 1 ryan ryan   8925 Mar 25 00:52 dbmmanage
-rw-rw-r-- 1 ryan ryan   1073 Mar 25 00:52 envvars
-rw-rw-r-- 1 ryan ryan   1073 Mar 25 00:52 envvars-std
-rwxr-xr-x 1 root root  17832 Mar 25 00:54 fcgistarter
-rwxr-xr-x 1 root root  48808 Mar 25 00:54 htcacheclean
-rwxr-xr-x 1 root root  35976 Mar 25 00:54 htdbm
-rwxr-xr-x 1 root root  22184 Mar 25 00:54 htdigest
-rwxr-xr-x 1 root root  35480 Mar 25 00:54 htpasswd
-rwxr-xr-x 1 root root 991792 Mar 25 00:54 httpd
-rwxr-xr-x 1 root root  17816 Mar 25 00:54 httxt2dbm
-rwxr-xr-x 1 root root  18368 Mar 25 00:54 logresolve
-rwxr-xr-x 1 root root  35464 Mar 25 00:54 rotatelogs
ryan@yangqi:/usr/local/apache2/bin$ sudo ./apachectl -k start
httpd (pid 29316) already running
ryan@yangqi:/usr/local/apache2/bin$ sudo ./apachectl -M
Loaded Modules:
 core_module (static)
 so_module (static)
 http_module (static)
 mpm_event_module (static)
 authn_file_module (shared)
 authn_core_module (shared)
 authz_host_module (shared)
 authz_groupfile_module (shared)
 authz_user_module (shared)
 authz_core_module (shared)
 access_compat_module (shared)
 auth_basic_module (shared)
 reqtimeout_module (shared)
 filter_module (shared)
 mime_module (shared)
 log_config_module (shared)
 env_module (shared)
 headers_module (shared)
 setenvif_module (shared)
 version_module (shared)
 unixd_module (shared)
 status_module (shared)
 autoindex_module (shared)
 dir_module (shared)
 alias_module (shared)
ryan@yangqi:/usr/local/apache2/bin$ 
```
```
<Directory />
    AllowOverride none
    Require all granted
</Directory>


</Directory>

#
# DirectoryIndex: sets the file that Apache will serve if a directory
# is requested.
#
<IfModule dir_module>
    DirectoryIndex index.html index.htm index.php
</IfModule>

    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz
    AddType application/x-httpd-php .php

root@yangqi:/etc/apache2/bin/# ./apachectl -k restart 
root@yangqi:/var/www/html/# vim index.html
This is www.yangqi.com
root@yangqi:/etc/apache2# curl 192.168.122.232/index.html
This is www.yangqi.com
root@yangqi:/etc/apache2# 
```
```
<VirtualHost *:80>
        ServerName www.yangqi.com
        DocumentRoot /var/www/dev
        ErrorLog /var/log/apache2/1/error.log
        CustomLog /var/log/apache2/1/access.log combined
</VirtualHost>
root@yangqi:/var/www/dev/# vim index.html
This is www.yangqi.com
root@yangqi:~# curl www.yangqi.com
This is www.yangqi.com
root@yangqi:~# 

```

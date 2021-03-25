```
        ServerName www.yangqi.com

        ServerAdmin <?>
        DocumentRoot /var/www/html
        <Directory /var/www/html>
                AllowOverride AuthConfig
                AuthName "yangqi.com user auth"
                Authtype Basic
                AuthUserFile /var/.htpasswd
                require valid-user
        </Directory>
root@yangqi:/etc/apache2/sites-enabled# htpasswd -cm /var/.htpasswd who
New password: 
Re-type new password: 
Adding password for user who
root@yangqi:/etc/apache2/sites-enabled# service apache2 restart
root@yangqi:/etc/apache2/sites-enabled# 
```

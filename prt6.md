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
```
<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	ServerName yangqi.com
	ServerAlias doc.yangqi.com

	ServerAdmin <?>
	DocumentRoot /var/www/html
	#<Directory /var/www/html>
	#	AllowOverride AuthConfig
	#	AuthName "yangqi.com user auth"
	#	Authtype Basic
	#	AuthUserFile /var/.htpasswd
	#	require valid-user
	#</Directory>
	RewriteEngine on
	RewriteCond %{HTTP_HOST} !^yangqi.com$
	RewriteRule ^/(.*)$ http://yangqi.com/$1 [R=301,L]
root@yangqi:/etc/apache2/sites-enabled# curl -x192.168.122.232:80 doc.yangqi.com
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://yangqi.com/">here</a>.</p>
<hr>
<address>Apache/2.4.41 (Ubuntu) Server at doc.yangqi.com Port 80</address>
</body></html>
root@yangqi:/etc/apache2/sites-enabled#
```

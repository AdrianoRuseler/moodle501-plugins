# Apache
- https://www.apache.org/

## Config
- https://docs.moodle.org/501/en/Apache

```bash
# https://docs.moodle.org/501/en/Apache#Routing
DocumentRoot /var/www/moodle/public
<Directory /var/www/moodle/public>
    AllowOverride None
    Require all granted
    FallbackResource /r.php
</Directory>

# https://docs.moodle.org/501/en/Apache
# The function slash arguments is required for various features 
# in Moodle to work correctly, as described in Using slash arguments. 
AcceptPathInfo On
				
# This enables missing files to be themed by Moodle 
ErrorDocument 404 /error/index.php
 
# This sends any 403 from apache through to the same page, but also
# overrides the http status with 404 instead for better security.
ErrorDocument 403 /error/index.php?code=404
				
# Hiding internal paths
RewriteEngine On
 
RewriteRule "(\/vendor\/)" - [F]
RewriteRule "(\/node_modules\/)" - [F]
RewriteRule "(^|/)\.(?!well-known\/)" - [F]
RewriteRule "(composer\.json)" - [F]
RewriteRule "(\.lock)" - [F]
RewriteRule "(\/environment.xml)" - [F]
Options -Indexes
RewriteRule "(\/install.xml)" - [F]
RewriteRule "(\/README)" - [F]
RewriteRule "(\/readme)" - [F]
RewriteRule "(\/moodle_readme)" - [F]
RewriteRule "(\/upgrade\.txt)" - [F]
RewriteRule "(\/UPGRADING\.md)" - [F]
RewriteRule "(phpunit\.xml\.dist)" - [F]
RewriteRule "(\/tests\/behat\/)" - [F]
RewriteRule "(\/fixtures\/)" - [F]
```
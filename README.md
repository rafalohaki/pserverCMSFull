# How to install the PServerCMS

The following tut is in progress

## SYSTEM REQUIREMENTS

requires PHP 5.4 or later; we recommend using the latest PHP version whenever possible.

## Step 0 Setup a WebServer + PHP + different extensions [Windows]

### DownloadList

- http://windows.php.net/downloads/releases/php-5.6.8-Win32-VC11-x64.zip
- http://www.apachehaus.com/cgi-bin/download.plx?dli=UVFcxlVVBFjTUd2aZRVT6pkVOpkVFVVca5GbCRVU
- For MSVCR110.dll Error, you have to download and install following http://www.microsoft.com/en-us/download/details.aspx?id=30679
- [ONLY FOR MsSQL] https://www.microsoft.com/en-us/download/details.aspx?id=20098 [Download Version 3.2]

## Setup basic Apache with default PHP

 Go to the apache/bin directory and type `httpd -k install` as administrator. than you can start the ApacheMonitor to check if the 
 Apache24 is listed and can be start.
 
 Now you have to add the following lines in your Apache `https.conf` (you can find it in the `conf` directory).
 
 ```ini
 LoadModule php5_module "c:/PHP/php5apache2_4.dll"
 <FilesMatch \.php$>
       SetHandler application/x-httpd-php
  </FilesMatch>
 
 # configure the path to php.ini
 PHPIniDir "C:/PHP"
 ```
 
 You you have to restart your Apache, to test if the PHP works.
 
 ## Enable PHP extensions
 
 Rename the `php.ini-production` in `php.ini` in your PHP-Directory.
 
 Add the following things in your `php.ini` file.
 
 ```ini
 extenions_dir = "ext"
 extension=php_curl.dll
 extension=php_gd2.dll
 extension=php_openssl.dll
 extension=php_pdo_mysql.dll ; if you work with a mysql DB
 extension=php_sockets.dll
 extension=php_pdo_sqlsrv_56_ts.dll # if you work with a mssql DB 
 ```
 
 If you work with a MsSQL DB you have to copy the `php_pdo_sqlsrv_56_ts.dll` from the download above, to the `ext` directory from your PHP.
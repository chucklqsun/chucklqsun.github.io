# Common Issue
1. if log file is not regenerated, please restart the process

## PHP from homebrew
//1. config:/private/etc/php-fpm.conf ,  /private/etc/php-fpm.d/www.conf
1. /usr/local/etc/php/7.1/php.ini
2. restart php-fpm
```
brew services restart php71
```
3. Error: “Primary script unknown” is below issue:
```
 fastcgi_param SCRIPT_FILENAME  /Users/bartowski/project/laravel/public$fastcgi_script_name;
```

## Install PHP extension
### stomp
1. 下载 $ wget http://pecl.php.net/get/stomp-1.0.5.tgz $ tar zxf stomp-1.0.5.tgz $ cd stomp-1.0.5 #通过phpize 生成编译所需配置文件 [注1]
```
$ /usr/bin/phpize
```
2. #编译安装三部曲: 1/configure 2/make 3/make install
```
先要安装brew install openssl
$ ./configure --enable-stomp --with-php-config=/usr/bin/php-config --with-openssl-dir=/usr/local/opt/openssl/
$ make
maybe then make install
```
3. modify /usr/local/etc/php/7.1/php.ini to add stomp.so

### PHP intl
brew install homebrew/php/php70-intl

### Warning: Module 'mcrypt' already loaded in Unknown on line 0
```
brew remove php71-mcrypt
rm  /usr/local/etc/php/7.1/conf.d/ext-mcrypt.ini
```

## Nginx from homebrew

Docroot is: /usr/local/var/www

The default port has been set in /usr/local/etc/nginx/nginx.conf to 8080 so that
nginx can run without sudo.

nginx will load all files in /usr/local/etc/nginx/servers/.

To have launchd start nginx now and restart at login:
  brew services start nginx
Or, if you don't want/need a background service you can just run:
  nginx

## MariaDB from homebrew

A "/etc/my.cnf" from another install may interfere with a Homebrew-built
server starting up correctly.

MySQL is configured to only allow connections from localhost by default

To connect:
    mysql -uroot

To have launchd start mariadb now and restart at login:
  brew services start mariadb
Or, if you don't want/need a background service you can just run:
  mysql.server start

## LDAP
brew install openldap lmdb
application: /usr/local/opt/openldap/
config:  /usr/local/etc/openldap/

/usr/libexec/slapd -d 255 -f /usr/local/etc/openldap/slapd.conf

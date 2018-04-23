FROM ubuntu:16.04
RUN apt-get update\
&& apt-get install wget -y\ 
&& wget http://cn2.php.net/distributions/php-7.2.4.tar.gz\
&& tar xzf php-7.2.4.tar.gz\
&& cd php-7.2.4/\
#install php dependencies
&& apt-get install build-essential gcc g++ autoconf libiconv-hook-dev libmcrypt-dev libxml2-dev libmysqlclient-dev libcurl4-openssl-dev libjpeg8-dev libpng12-dev libfreetype6-dev libssl-dev -y\
&& if [ -f /usr/lib/x86_64-linux-gnu/libssl.so ] && [ ! -f  /usr/lib/libssl.so ]; then ln -s /usr/lib/x86_64-linux-gnu/libssl.so /usr/lib; fi\ 
&& ./configure --enable-fpm --enable-pcntl --enable-mysqlnd --enable-opcache --enable-sockets --enable-sysvmsg --enable-sysvsem  --enable-sysvshm --enable-shmop --enable-zip --enable-ftp --enable-soap --enable-xml --enable-mbstring --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-pcre-regex --with-iconv --with-zlib --with-gd --with-openssl --with-mhash --with-xmlrpc --with-curl --with-imap-ssl --without-pear  --disable-phar\
# compile
&& make\
&& make install\
# install pear
&& wget http://pear.php.net/go-pear.phar \
&& php go-pear.phar\
##install composer
&& wget https://getcomposer.org/installer\
&& php installer\
&& php -r "unlink('installer');" \
&& mv composer.phar /usr/local/bin/composer \
&& composer config -g repo.packagist composer https://packagist.phpcomposer.com

EXPOSE 9000
CMD php-fpm && bash


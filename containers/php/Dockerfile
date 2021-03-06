FROM base/archlinux
MAINTAINER David Parrish <daveparrish@gmail.com>

# Install PHP
RUN pacman -Syq --noconfirm --needed php-fpm php-sqlite php-gd \
    >/dev/null 2>/dev/null

# Configure PHP
RUN sed -i 's/;extension=pdo_mysql.so/extension=pdo_mysql.so/g' /etc/php/php.ini
RUN sed -i 's/;extension=pdo_sqlite.so/extension=pdo_sqlite.so/g' /etc/php/php.ini
RUN sed -i 's/;extension=gd.so/extension=gd.so/g' /etc/php/php.ini
RUN sed -i 's/;extension=openssl.so/extension=openssl.so/g' /etc/php/php.ini
RUN sed -i 's/upload_max_filesize = 2M/upload_max_filesize = 8M/g' /etc/php/php.ini

# Configure PHP-FPM listening port
RUN sed -i '/^listen/c \
listen = 0.0.0.0:9000' /etc/php/php-fpm.conf

# mariadb required for mysql commandline
RUN pacman -Syq --needed --noconfirm base-devel git jshon mariadb \
    >/dev/null 2>/dev/null
# Turn on mysql client auto-complete
RUN sed -i 's/no-auto-rehash/auto-rehash/g' /etc/mysql/my.cnf

# Allow nginx to find service
EXPOSE 9000

# Add script for running service
ADD start_php_fpm.sh /opt/start_php_fpm.sh

# Move root directory
#RUN sed -i '/^;chdir/c \
#chdir = /code/drupal' /etc/php/php-fpm.conf

# Place the log location
#RUN sed -i '/^;error_log/c \
#error_log = /log/php-fpm.log' /etc/php/php-fpm.conf
#RUN sed -i '/^;access.log/c \
#access.log = /log/$pool.access.log' /etc/php/php-fpm.conf
#RUN sed -i '/^;slowlog/c \
#slowlog = log/$pool.log.slow' /etc/php/php-fpm.conf

# vi: set tabstop=4 expandtab :

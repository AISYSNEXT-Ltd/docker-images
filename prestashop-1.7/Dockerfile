FROM arm64v8/php:7.4-apache
WORKDIR /var/www/html

RUN a2enmod rewrite
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install tar gzip zip unzip bzip2 wget 
RUN apt-get -y install libzip-dev libpng-dev zlib1g-dev libonig-dev libcurl4-openssl-dev pkg-config libxml2-dev
RUN docker-php-ext-install zip gd json mbstring curl xml intl pdo pdo_mysql opcache
RUN docker-php-ext-enable intl zip gd json mbstring curl xml pdo pdo_mysql opcache


RUN wget https://github.com/PrestaShop/PrestaShop/releases/download/1.7.8.7/prestashop_1.7.8.7.zip
RUN unzip -o prestashop_1.7.8.7.zip && unzip -o prestashop.zip
RUN rm -rf prestashop_1.7.8.7.zip prestashop.zip Install_PrestaShop.html

RUN chmod -R 0775 /var/www/html/var/logs \
/var/www/html/var/cache \
/var/www/html/config \
/var/www/html/img \
/var/www/html/mails \
/var/www/html/modules \
/var/www/html/translations \
/var/www/html/upload \
/var/www/html/download \
/var/www/html/app/config \
/var/www/html/app/Resources/translations \
/var/www/html/img \
/var/www/html/admin \
/var/www/html/themes


RUN touch /usr/local/etc/php/php.ini && echo "short_open_tag=FALSE" >> /usr/local/etc/php/php.ini
RUN echo "allow_url_fopen = On" >> /usr/local/etc/php/php.ini
RUN echo "allow_url_include = Off" >> /usr/local/etc/php/php.ini

RUN echo "max_execution_time = 200" >> /usr/local/etc/php/php.ini
RUN echo "memory_limit = 512M" >> /usr/local/etc/php/php.ini
RUN echo "post_max_size = 128M" >> /usr/local/etc/php/php.ini
RUN echo "upload_max_filesize = 100M" >> /usr/local/etc/php/php.ini


EXPOSE 80
EXPOSE 443
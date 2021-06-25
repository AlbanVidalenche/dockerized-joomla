FROM debian:buster
RUN  apt update && apt-get install -y  --no-install-recommends\
 php \
 php-gd \
 php-xmlrpc \
 php-fpm \ 
 php-curl \
 php-intl \
 php-imagick \
 php-mysql \
 php-zip \
 php-xml \
 php-mbstring \
 php-bcmath \
 unzip \
 wget &&\
 wget https://downloads.joomla.org/fr/cms/joomla3/3-9-27/Joomla_3-9-27-Stable-Full_Package.zip?format=zip &&\
 unzip Joomla.zip -d /var/www/joomla &&\
 chown -R www-data:www-data /var/www/joomla
RUN service php7.3-fpm start
RUN service php7.3-fpm stop
VOLUME /var/www/html
COPY www.conf /etc/php/7.3/fpm/pool.d/www.conf
EXPOSE 9000
CMD ["php-fpm7.3","-F"]
 
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
 php-bcmath 
RUN service php7.3-fpm start
RUN service php7.3-fpm stop
COPY www.conf /etc/php/7.3/fpm/pool.d/www.conf
EXPOSE 9000
CMD ["php-fpm7.3","-F"]
 
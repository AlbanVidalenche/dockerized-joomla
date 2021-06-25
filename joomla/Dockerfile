FROM debian:buster
RUN  apt update && apt-get install -y  --no-install-recommends\
 ca-certificates \
 unzip \
 wget &&\
 mkdir -p /var/www/joomla && \
 wget -O joomla.zip https://downloads.joomla.org/fr/cms/joomla3/3-9-27/Joomla_3-9-27-Stable-Full_Package.zip?format=zip &&\
 unzip joomla.zip -d /var/www/joomla &&\
 chown -R www-data:www-data /var/www/joomla
VOLUME /var/www/joomla



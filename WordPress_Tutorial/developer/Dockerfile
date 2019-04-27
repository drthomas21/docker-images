#Official Repository: https://hub.docker.com/_/ubuntu/
FROM ubuntu:bionic
ENV BUILD_NAME="WordPress Tutorial 7.2" \
    BUILD_VERSION=1.0.0j \
    APACHE_PATH=/var/www

#Update APT-GET cache
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential gperf software-properties-common apt-utils language-pack-en-base

RUN LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install apt-utils vim curl sendmail \
    zip imagemagick mysql-client memcached apache2 libapache2-mod-php7.2 nano phing\
    pkg-config composer libmcrypt-dev telnet \
    php7.2 php7.2-curl php7.2-gd php-imagick php7.2-json php7.2-xml php7.2-mbstring \
    php-memcached php7.2-mysqli php7.2-mysqlnd php-xdebug php7.2-zip php7.2-xmlrpc \
    php7.2-redis php7.2-intl php7.2-tidy \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

#Making sure the correct version of PHP is selected
RUN update-alternatives --set php /usr/bin/php7.2

#Mount configurations
ADD etc /etc
ADD var /var
ADD execute.sh /var/exec/execute.sh

#Apache Configuration
RUN a2enmod setenvif proxy_http rewrite php7.2 headers ssl authz_groupfile && a2ensite wordpress community

#Open Ports
EXPOSE 80/TCP 443/TCP 11211/TCP

#Start up services
CMD ["/bin/bash","/var/exec/execute.sh"]

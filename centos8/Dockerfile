ARG CENTOS_VERSION=8
FROM centos:${CENTOS_VERSION}

ARG PHP_VERSION=7.3
ARG CENTOS_VERSION=8

# seems to be an issue in the base image?
RUN cd /var/lib; rm -f __db*; rpm --rebuilddb; cp -afv rpmrebuild*/* rpm/
RUN yum upgrade -y && \
  yum install -y http://rpms.remirepo.net/enterprise/remi-release-${CENTOS_VERSION}.rpm && \
  dnf module install php:remi-${PHP_VERSION} -y && \
  yum clean all
RUN yum install -y \
  php-common \
  php-xmlrpc \
  php-pecl-memcached \
  php-pecl-memcache \
  php-mysqlnd \
  php-pear \
  php-gd \
  php-mbstring \
  php-cli \
  php-process \
  php-opcache \
  php-pecl-redis \
  php-bcmath \
  php-pecl-gearman \
  php-soap \
  php-zip \
  ImageMagick \
  php-pecl-imagick && yum clean all

RUN useradd -u 33 -g 33 www-data

USER www-data

CMD ["php"]

FROM php:5.5.30-fpm
RUN mkdir -p /data/sites && \
	chown www-data:www-data /data/sites
ADD etc /etc
RUN apt-get update && \
	apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng12-dev \
		libmcrypt-dev && \
	docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
	docker-php-ext-install iconv mcrypt mysqli gd && \
	apt-get clean &&  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

VOLUME ["/data"]
CMD ["php-fpm"]
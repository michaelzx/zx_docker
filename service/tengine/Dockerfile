FROM michaelzx/debian:latest
MAINTAINER Michael.Z "mail@zhangxiao.org"

# Let the conatiner know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

#Declare tengine version environment variable
ENV TENGINE_VERSION=2.1.1
#Install basic requirements
RUN apt-get install -y gcc libssl-dev libpcre3-dev make
#Create nginx_http_user for nginx
RUN adduser \
	--disabled-login \
	--no-create-home \
	--gecos 'Tengine_Http_User' \
	nginx_http_user


WORKDIR /tmp/
#Download tengine and 
RUN wget http://tengine.taobao.org/download/tengine-$TENGINE_VERSION.tar.gz && \
	tar zxvf tengine-$TENGINE_VERSION.tar.gz && \
	rm tengine-$TENGINE_VERSION.tar.gz

WORKDIR /tmp/tengine-$TENGINE_VERSION

RUN ./configure \
	--prefix=/etc/nginx \
	--conf-path=/etc/nginx/nginx.conf \
	--sbin-path=/usr/bin/nginx \
	--user=nginx_http_user \
	--group=nginx_http_user && \
	make && \
	make install && \
	echo "\ndaemon off;">>/etc/nginx/nginx.conf && \
	chown -R nginx_http_user /etc/nginx

RUN apt-get clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#WORKDIR /etc/nginx/sbin/

EXPOSE 80 443

CMD ["nginx"]
FROM michaelzx/debian:jessie
MAINTAINER Michael.Z "mail@zhangxiao.org"

# Let the conatiner know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

#Declare tengine version environment variable
ENV TENGINE_VERSION=2.1.1
#Install basic requirements
RUN apt-get install -y gcc libssl-dev libpcre3-dev make && \
#Create nginx_http_user for nginx
	adduser \
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
	# echo "\ndaemon off;">>/etc/nginx/nginx.conf && \
	chown -R nginx_http_user /etc/nginx && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#WORKDIR /etc/nginx/sbin/
ADD ./etc/nginx/nginx.conf /etc/nginx/
#RUN mkdir -p /data/sites
#RUN mkdir -p /data/sites_conf
#RUN chmod -R +x /data/sites
#RUN chmod -R +x /data/sites_conf
#RUN chown -R nginx_http_user /data/sites
#RUN chown -R nginx_http_user /data/sites_conf
#ADD ./data/sites/* /data/sites/
#ADD ./data/sites_conf/* /data/sites_conf/
#RUN cd /data/ && ls
#RUN cd /data/sites/ && ls
#RUN cd /data/sites_conf/ &&ls

EXPOSE 80 443

VOLUME ["/data"]

CMD ["nginx"]
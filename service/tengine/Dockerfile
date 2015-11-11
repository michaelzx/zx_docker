#base image
FROM michaezx/debian:latest
#作者信息
MAINTAINER Michael.Z "mail@zhangxiao.org"

# Let the conatiner know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get install -y gcc libssl-dev libpcre3-dev make
RUN adduser --disabled-login --gecos 'Tengine' nginx 

WORKDIR /home/nginx
RUN wget http://tengine.taobao.org/download/tengine-2.1.1.tar.gz
RUN tar zxvf tengine-2.1.1.tar.gz
RUN rm tengine-2.1.1.tar.gz
WORKDIR /home/nginx/tengine-2.1.1
RUN ./configure
RUN make
RUN make install
RUN apt-get clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /home/nginx/*
WORKDIR /usr/local/nginx/sbin/
CMD ["./nginx", "-g", "daemon off;"]

EXPOSE 80
EXPOSE 443
#base image
FROM daocloud.io/zx0211/debian
#作者信息
MAINTAINER Michael.Z "mail@zhangxiao.org"

ENV DEBIAN_FRONTEND noninteractive

RUN adduser --disabled-login --gecos 'Tengine' nginx

WORKDIR /home/nginx
RUN wget http://tengine.taobao.org/download/tengine-2.1.1.tar.gz
RUN tar xvf tengine-2.1.1.tar.gz
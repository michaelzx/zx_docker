FROM debian:jessie

MAINTAINER Michael.Z <mail@zhangxiao.org>
#将文件<src>拷贝到container的文件系统对应的路径<dest>
#所有拷贝到container中的文件和文件夹权限为0755,uid和gid为0
#如果文件是可识别的压缩格式，则docker会帮忙解压缩
ADD etc /etc

#用来设置环境变量
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
	#apt-get upgrade -y && \
	#apt-get install -y ca-certificates inotify-tools nano pwgen supervisor unrar unzip wget && \
	apt-get clean && \
	echo -n > /var/lib/apt/extended_states

RUN mkdir /config /data

RUN useradd -u 500 core

ADD config /config

RUN chmod +x /config/loop
#container启动时执行的命令，但是一个Dockerfile中只能有一条CMD命令，多条则只执行最后一条CMD.
CMD /config/loop
#container启动时执行的命令，但是一个Dockerfile中只能有一条ENTRYPOINT命令，如果多条，则只执行最后一条
#ENTRYPOINT没有CMD的可替换特性
#ENTRYPOINT ["memcached"]
#使用哪个用户跑container
#USER daemon
#container内部服务开启的端口。主机上要用还得在启动container时，做host-container的端口映射：
EXPOSE 80
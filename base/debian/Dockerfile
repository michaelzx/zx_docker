#base image
FROM debian:jessie
#作者信息
MAINTAINER Michael.Z <mail@zhangxiao.org>
#将文件<src>拷贝到container的文件系统对应的路径<dest>
#所有拷贝到container中的文件和文件夹权限为0755,uid和gid为0
#如果文件是可识别的压缩格式，则docker会帮忙解压缩
ADD etc /etc
#用来设置环境变量
#这个引导参数控制用于安装程序的用户界面的类型。noninteractive表示【非交互式】
ENV DEBIAN_FRONTEND noninteractive

#获得最近的软件包的列表
RUN apt-get update && \
	#upgrade 是升级【已安装】的所有软件包
	#升级之后的版本就是本地索引里的，因此，在执行 upgrade 之前一定要执行 update, 这样才能是最新的。
	#这里的参数-y不知道是啥意思，知道的朋友请告知一下
	#a-certificates inotify-tools nano pwgen supervisor unrar unzip wget && \
	apt-get install -y wget && \
	apt-get clean && \
	echo -n > /var/lib/apt/extended_states && \
	mkdir /config /data && \
	useradd -u 500 core
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
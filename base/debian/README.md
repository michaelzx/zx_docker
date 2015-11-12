#说明
本镜像以debian:jessie为基础，做了以下工作： 

* 将sources.list替换成`阿里云`的镜像，方便在国内使用apt-get安装和更新软件
* 从`阿里云`上更新了软件资源列表（apt-get update）  
* 安装了 wget

#使用Dockerfile构建镜像
```
$ cd path/base/debian/
$ docker build --rm -t michaelzx/debian .
```
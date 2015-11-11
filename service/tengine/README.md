#说明
本进项是基于michaelzx/debian，具体说明查看该项目说明

#使用Dockerfile构建镜像
```
$ cd Dockerfile所在文件夹
$ docker build --rm -t some-image-name .
```
#或者直接从Docker Hub上pull

```
$ docker pull michaelzx/debian
```

#创建本镜像容器
```
$ docker run -d -p 8080:80  --name=some-container-name image-name
```
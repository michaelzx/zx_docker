#说明
本进项是基于michaelzx/debian，具体说明查看该项目说明

#使用Dockerfile构建镜像
```
$ cd path/base/debian/
$ docker build --rm -t michaelzx/tengine .
```

#创建本镜像容器
```
$ docker run -d -p 8080:80  --name=tngx michaelzx/tengine
```
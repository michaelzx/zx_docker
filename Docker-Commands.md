#Docker-Commands

##镜像和容器的清理

###删除所有运行中的容器

```
$ docker kill $(docker ps -q)
```

###删除所有停止的容器

```
$ docker rm $(docker ps -a -q)
```

###删除所有没有tag和挂起的镜像

```
docker rmi $(docker images -q -f dangling=true)
```

###删除所有镜像

```
docker rmi $(docker images -q)
```
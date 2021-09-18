# Docker 使用方法

## 镜像相关

获取镜像

```bash
docker pull ubuntu
```

列出本机上的镜像

```bash
docker images
```

删除镜像

```bash
docker rmi hello-world
```

## 后台启动容器

后台启动容器

```bash
docker run -itd --name ubuntu-test ubuntu /bin/bash
```

查看所有容器

```bash
docker ps -a
```

停止容器

```bash
docker stop ubuntu-test
```

启动已停止运行的容器

```bash
docker start/restart ubuntu-test
```

删除启动的容器

```bash
docker rm ubuntu-test
```

## 进入容器

进入容器

```bash
docker exec -it ubuntu-test /bin/bash
```

退出容器

```bash
exit
```

## 从 host 拷贝文件到 docker

```bash
docker cp dCube/ ubuntu-test:/home/
```


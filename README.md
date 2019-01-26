
# docker_tips
------

学习docker过程中的一些笔记，操作系统基于CentOS7.4

### 安装docker-ce
[官方文档](https://docs.docker.com/install/linux/docker-ce/centos/)

```bash
# 开机自启
systemctl enable docker
```

### 基本命令
```bash
# 列出运行中的容器
docker ps

# 列出所有容器
docker ps -a

# 列出所有镜像
docker images

# 进入运行中的容器，执行指定命令
docker exec -it CONTAINER COMMAND [ARG...]

# 移除容器
docker rm CONTAINER [CONTAINER...]

# 移除镜像
docker rmi IMAGE [IMAGE...]
```
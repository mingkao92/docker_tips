# docker_tips

学习docker过程中的一些笔记，操作系统为CentOS7.4

### 基本概念
- 容器化：使用Linux容器来部署应用
- 镜像：集成应用和运行环境文件的可执行包
- 容器：镜像的运行实例

### 安装
[官方文档](https://docs.docker.com/install/linux/docker-ce/centos/)

```bash
# 开机自启
systemctl enable docker
```

### 基本命令
```bash
# 查看信息
docker info

# 列出所有镜像
docker images

# 列出运行中的容器
docker ps

# 列出所有容器
docker ps -a

# 进入运行中的容器，执行指定命令
docker exec -it CONTAINER COMMAND [ARG...]

# 移除容器
docker rm CONTAINER [CONTAINER...]

# 移除所有容器
docker rm $(docker ps -aq)

# 移除镜像
docker rmi IMAGE [IMAGE...]

# 移除所有容器
docker rmi $(docker images -q)
```

### Dockerfile
```bash
# 从当前目录的Dockerfile构建镜像
docker build -t NAME[:TAG] .
```

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
表示方法：
> * 镜像 IMAGE
> REPOSITORY[:TAG] # 未指定TAG取latest
> IMAGE ID
> * 容器 CONTAINER
> NAMES # 未命名则随机生成
> CONTAINER ID
> * 网络 NETWORK
> NAME
> NETWORK ID

```bash
# 查看安装信息
docker info

# 查看安装版本
docker --version

# 拉取镜像
docker pull IMAGE

# 列出本地所有镜像
docker images

# 查看本地镜像历史
docker history IMAGE

# 创建指定名称容器
docker create --name NAME IMAGE

# 运行容器
docker start CONTAINER

# 运行容器并将绑定输出
docker start -a CONTAINER

# 列出运行中的容器
docker ps

# 列出所有容器
docker ps -a

# 查看容器端口映射
docker port CONTAINER

# 进入运行中的容器，执行指定命令
docker exec -it CONTAINER COMMAND [ARG...]

# 移除容器
docker rm CONTAINER [CONTAINER...]

# 移除镜像
docker rmi IMAGE [IMAGE...]

# 移除所有容器
docker rm $(docker ps -aq)

# 移除所有镜像
docker rmi $(docker images -q)

# 显示docker网络
docker network ls

# 显示网络详细信息
docker network inspect NETWORK
```

### Dockerfile
```bash
# 从当前目录的Dockerfile构建镜像
docker build -t IMAGE .
```

### Docker Compose
[官方安装文档](https://docs.docker.com/compose/install/)

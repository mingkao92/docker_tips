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

#### Docker Compose
[官方文档](https://docs.docker.com/compose/install/)


### 基本命令
表示方法
> * 镜像 IMAGE
> REPOSITORY[:TAG] # 未指定TAG为latest
> IMAGE ID
> * 容器 CONTAINER
> NAMES # 未命名则随机生成
> CONTAINER ID
> * 网络 NETWORK
> NAME
> NETWORK ID
> * 仓库 REGISTRY
> * 仓库用户名 REGISTRY_USERNAME
> * 仓库密码 REGISTRY_PASSWORD
> * hosts对 HOST_PAIR
> * volume对 VOLUME_PAIR
> * port对 PORT_PAIR


安装信息
```bash
# 查看client版本
docker --version

# 查看安装信息
docker version
```

镜像和容器
```
# 从当前目录下的Dockerfile构建镜像
docker build -t IMAGE .

# 列出本地所有镜像
docker images

# 创建并启动容器
docker run --add-host HOST_PAIR --volume VOLUME_PAIR --publish PORT_PAIR --name CONTAINER -d IMAGE

# 列出运行中的容器
docker ps

# 列出所有容器
docker ps -a

# 进入运行中的容器，执行shell命令
docker exec -it CONTAINER sh

# 输出并跟踪容器日志
docker logs -f --tail=10 CONTAINER

# 运行容器
docker start CONTAINER [CONTAINER...]

# 停止容器
docker stop CONTAINER [CONTAINER...]

# 重启容器
docker restart CONTAINER [CONTAINER...]

# 移除镜像
docker rmi IMAGE [IMAGE...]

# 移除虚悬镜像
docker rmi $(docker images -q -f dangling=true)

# 移除容器
docker rm CONTAINER [CONTAINER...]

# 强制移除容器
docker rm -f CONTAINER [CONTAINER...]
```

# 容器内执行宿主机docker命令

### 使用场景
单台服务器，需要通过容器来进行隔离，但又必须用到宿主机的docker命令

### 使用方法
通过文件映射的方式，将docker映射到容器内部
```bash
docker run -it -v /host/docker/somefile:/container/docker/somefile busybox sh
```

举例：
> 获取宿主机安装信息
```
[root@localhost ~]# docker version
Client: Docker Engine - Community
 Version:           19.03.1
 ...
 OS/Arch:           linux/amd64
```

> 下载相应static-docker-binary<br />
> static-docker-binary不能用宿主机$(which docker)所对应文件，不然会报依赖未找到<br />
上面宿主机对应static-docker-binary下载链接为<br />
https://download.docker.com/linux/static/stable/x86_64/docker-19.03.1.tgz
```bash
curl https://download.docker.com/linux/static/stable/x86_64/docker-19.03.1.tgz | tar -zx -C /root/tools
chown root:root /root/tools/docker/docker
```

> 拉取私有镜像仓库的镜像<br />
> 如果有需要，要在宿主机配置认证信息并映射到容器内部
```
-v /root/.docker/config.json:/root/.docker/config.json
```

> 最终命令
```bash
docker run -it \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /root/.docker/config.json:/root/.docker/config.json \
    -v /root/tools/docker/docker:/usr/bin/docker \
    busybox sh
```

### 其他实现方案
可以借助ssh容器，通过ssh协议来连接服务器（需要add_host映射host:$(ifconfig docker0 | awk '/inet/{print $2}')）

### 参考链接

- [docker run](https://docs.docker.com/engine/reference/commandline/run/)

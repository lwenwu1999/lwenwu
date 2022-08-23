# Docker概述

Docker是一个用于开发，发布和运行应用程序的开放平台。Docker使您能够将应用程序与基础架构分开，从而可以快速交付软件。借助Docker，您可以以与管理应用程序相同的方式来管理基础架构。通过利用Docker的方法来快速交付，测试和部署代码，您可以大大减少编写代码和在生产环境中运行代码之间的延迟。

## Docker平台

Docker提供了在松散隔离的环境（称为容器）中打包和运行应用程序的功能。隔离和安全性使您可以在给定主机上同时运行多个容器。容器是轻量级的，因为它们不需要管理程序的额外负载，而是直接在主机的内核中运行。这意味着与使用虚拟机相比，在给定的硬件组合上可以运行更多的容器。您甚至可以在实际上是虚拟机的主机中运行Docker容器！

Docker提供了工具和平台来管理容器的生命周期：

- 使用容器开发应用程序及其支持组件。
- 容器成为分发和测试应用程序的单元。
- 准备就绪后，可以将应用程序作为容器或协调服务部署到生产环境中。无论您的生产环境是本地数据中心，云提供商还是两者的混合，其工作原理都相同。

## Docker引擎

*Docker Engine*是具有以下主要组件的客户端-服务器应用程序：

- 服务器是一种长期运行的程序，称为守护程序进程（ `dockerd`命令）。
- REST API，它指定程序可以用来与守护程序进行通信并指示其操作的接口。
- 命令行界面（CLI）客户端（`docker`命令）。

![image-20201119124650150](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225652.png)

CLI使用Docker REST API通过脚本或直接CLI命令控制或与Docker守护程序交互。许多其他Docker应用程序都使用基础API和CLI。

守护程序创建和管理Docker*对象*，例如图像，容器，网络和卷。

> **注意**：Docker已获得开源Apache 2.0许可证的许可。

我可以将Docker用于什么？

**快速，一致地交付您的应用程序**

Docker通过允许开发人员使用提供您的应用程序和服务的本地容器在标准化环境中工作，从而简化了开发生命周期。容器非常适合持续集成和持续交付（CI / CD）工作流程。

请考虑以下示例方案：

- 您的开发人员在本地编写代码，并使用Docker容器与同事共享他们的工作。
- 他们使用Docker将其应用程序推送到测试环境中，并执行自动和手动测试。
- 当开发人员发现错误时，他们可以在开发环境中对其进行修复，然后将其重新部署到测试环境中以进行测试和验证。
- 测试完成后，将修补程序推送给生产环境就像将更新的映像推送到生产环境一样简单。

**响应式部署和扩展**

Docker基于容器的平台允许高度可移植的工作负载。Docker容器可以在开发人员的本地笔记本电脑上，数据中心中的物理或虚拟机，云提供商或混合环境中运行。

Docker的可移植性和轻量级的特性还使您可以轻松地动态管理工作负载，并根据业务需求指示实时扩展或拆除应用程序和服务。

**在同一硬件上运行更多工作负载**

Docker轻巧快速。它为基于虚拟机管理程序的虚拟机提供了可行且经济高效的替代方案，因此您可以利用更多的计算能力来实现业务目标。Docker非常适合高密度环境以及中小型部署，而您需要用更少的资源做更多的事情。

## Docker架构

Docker使用客户端-服务器架构（C/S）。Docker*客户端*与Docker*守护进程*进行对话，该*守护进程*完成了构建，运行和分发Docker容器的繁重工作。Docker客户端和守护程序*可以* 在同一系统上运行，或者您可以将Docker客户端连接到远程Docker守护程序。Docker客户端和守护程序在UNIX套接字或网络接口上使用REST API进行通信。

![image-20201119124727100](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225653.png)

## Docker守护程序

Docker守护程序（`dockerd`）侦听Docker API请求并管理Docker对象，例如图像，容器，网络和卷。守护程序还可以与其他守护程序通信以管理Docker服务。

## Docker客户端

Docker客户端（`docker`）是许多Docker用户与Docker交互的主要方式。当您使用诸如之类的命令时`docker run`，客户端会将这些命令发送到`dockerd`，以执行这些命令。该`docker`命令使用Docker API。Docker客户端可以与多个守护程序通信。

## Docker注册表

Docker*注册表*存储Docker映像。Docker Hub是任何人都可以使用的公共注册表，并且默认情况下，Docker已配置为在Docker Hub上查找映像。您甚至可以运行自己的私人注册表。

使用`docker pull`或`docker run`命令时，所需的图像将从配置的注册表中提取。使用该`docker push`命令时，会将映像推送到配置的注册表。



容器是图像的可运行实例。您可以使用Docker API或CLI创建，启动，停止，移动或删除容器。您可以将容器连接到一个或多个网络，将存储连接到它，甚至根据其当前状态创建一个新映像。

默认情况下，容器与其他容器及其主机之间的隔离度相对较高。您可以控制容器的网络，存储或其他基础子系统与其他容器或与主机的隔离程度。

容器由其映像以及在创建或启动时为其提供的任何配置选项定义。删除容器后，未存储在永久性存储中的状态更改将消失。

## 比较容器和虚拟机

容器和虚拟机具有相似的资源隔离和分配优势，但功能不同，因为容器虚拟化操作系统而不是硬件。更方便携带，效率更高。

![image-20201119124802492](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225654.png)

## 容器

容器是应用层的抽象，它将代码和依赖项打包在一起。多个容器可以在同一台机器上运行，并与其他容器共享操作系统内核，每个容器都作为用户空间中的独立进程运行。容器比虚拟机占用更少的空间（容器映像的大小通常是几十MB），可以处理更多的应用程序，需要更少的虚拟机和操作系统。

## 虚拟机

虚拟机（vm）是物理硬件的抽象，将一台服务器转换成多台服务器。hypervisor允许多个vm在一台机器上运行。每个虚拟机都包含一个操作系统的完整副本、应用程序、必要的二进制文件和库—占用了数十GB的空间。vm的启动速度也很慢。

Docker为什么比VM快？

1.Docker有着比虚拟机更少的抽象层。

2.Docker利用的是宿主机的内核，VM需要完整Guest OS。

新建一个容器时，Docker不需要像虚拟机一样重新加载一个操作系统内核，避免引导。

虚拟机加载Guest OS是分钟级别，Docker利用宿主机操作系统，秒级。

![image-20201119124822492](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225655.png)

![image-20201119124837467](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225656.png)

## 底层技术

Docker用[Go编程语言](https://golang.org/)编写，并利用Linux内核的多个功能来交付其功能。

## 命名空间

Docker使用一种称为`namespaces`提供*容器*的隔离工作区的技术。运行容器时，Docker会为该容器创建一组 *名称空间*。

这些名称空间提供了一层隔离。容器的每个方面都在单独的名称空间中运行，并且其访问仅限于该名称空间。

Docker Engine在Linux上使用以下名称空间：

- **的`pid`命名空间：**进程隔离（PID：进程ID）。
- **该`net`命名空间：**管理网络接口（NET：网络）。
- **该`ipc`命名空间：**管理访问IPC资源（IPC：进程间通信）。
- **该`mnt`命名空间：**管理文件系统挂载点（MNT：摩）。
- **该`uts`命名空间：**隔离内核和版本标识符。（UTS：Unix时间共享系统）。

## 对照组

Linux上的Docker引擎还依赖于另一种称为*控制组* （`cgroups`）的技术。cgroup将应用程序限制为一组特定的资源。控制组允许Docker Engine将可用的硬件资源共享给容器，并有选择地实施限制和约束。例如，您可以限制特定容器可用的内存。

## 联合文件系统

联合文件系统或UnionFS是通过创建图层进行操作的文件系统，使其非常轻便且快速。Docker Engine使用UnionFS为容器提供构建模块。Docker Engine可以使用多个UnionFS变体，包括AUFS，btrfs，vfs和DeviceMapper。

## 容器格式

Docker Engine将名称空间，控制组和UnionFS组合到一个称为容器格式的包装器中。默认容器格式为`libcontainer`。将来，Docker可以通过与BSD Jails或Solaris Zones等技术集成来支持其他容器格式。



# 安装Docker

Docker文档：

https://docs.docker.com/get-docker/

![image-20201119124911354](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225657.png)

![image-20201119124941909](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225658.png)

## 安装Docker引擎

先决条件：

操作系统要求：要安装Docker引擎，需要CentOS 7的维护版本。不支持或测试存档版本。

必须启用centos-extras存储库。默认情况下该存储库是启用的，但是如果您已经禁用了它，则需要重新启用它。

安装gcc相关环境

```
yum -y install gcc
yum -y install gcc-c++
```

### 1.卸载旧版本

```shell
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

如果yum报告没有安装这些包，也是可以的。

/var/lib/docker/的内容，包括镜像、容器、卷和网络。Docker引擎包现在称为Docker -ce

### 2.安装基础包

```shell
yum install -y yum-utils
```

安装 yum-utils 包(它提供 yum-config-manager 实用工具)并设置稳定存储库。

### 3.添加镜像仓库

```shell
默认国外源：
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
阿里云：    
yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

### 4.更新yum软件包索引

```shell
yum makecache fast
```

### 5.安装 Docker引擎

```shell
yum install docker-ce docker-ce-cli containerd.io
```

安装特定版本的Docker：

```shell
yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
```

### 6.启动并加入开机自启动

```shell
systemctl start docker
systemctl enable docker
```

判断是否安装成功：

```shell
[root@localhost ~]# docker version
Client: Docker Engine - Community
 Version:           **19.03.13**
 API version:       1.40
 Go version:        **go1.13.15**
 Git commit:        4484c46d9d
 Built:             Wed Sep 16 17:03:45 2020
 OS/Arch:           linux/amd64
 Experimental:      false

**Server: Docker Engine - Community**
 Engine:
  Version:          19.03.13
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.13.15
  Git commit:       4484c46d9d
  Built:            Wed Sep 16 17:02:21 2020
  OS/Arch:          **linux/amd64**
  Experimental:     false
 containerd:
  Version:          1.3.7
  GitCommit:        8fba4e9a7d01810a393d5d25a3621dc101981175
 runc:
  Version:          1.0.0-rc10
  GitCommit:        dc9208a3303feef5b3839f4323d9beb36df0a9dd
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683
[root@localhost ~]# 
```

### 7.测试hello-world

通过运行 hello-world 镜像来验证 Docker Engine 安装是否正确。

```shell
docker run hello-world
```

```shell
[root@localhost ~]# docker run hello-world
Unable to find image 'hello-world:latest' locally   #寻找镜像
latest: Pulling from library/hello-world  #从library远程拉取hello-world镜像
0e03bdcc26d7: Pull complete 
Digest: sha256:8c5aeeb6a5f3ba4883347d3747a7249f491766ca1caa47e5da5dfcf6b9b717c0
Status: Downloaded newer image for hello-world:latest

Hello from Docker!   #Docker安装成功
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

### 8.查看hello-world镜像

```shell
[root@localhost ~]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              bf756fb1ae65        9 months ago        13.3kB
[root@localhost ~]#
```

### 9.卸载 Docker 引擎

卸载 Docker Engine、 CLI 和 Containerd 软件包:

```shell
yum remove docker-ce docker-ce-cli containerd.io
```

不会自动删除主机上的映像、容器、卷或自定义配置文件。您必须手动删除任何已编辑的配置文件。删除所有镜像，容器和卷:

```shell
rm -rf /var/lib/docker
```

## 配置阿里云镜像加速

![image-20201119125009408](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225659.png)

### 1.找到镜像加速器

![image-20201119125039567](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225700.png)

### 2.配置镜像加速器

针对Docker客户端版本大于 1.10.0 的用户

您可以通过修改daemon配置文件/etc/docker/daemon.json来使用加速器

```shell
sudo mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://gnxq79wc.mirror.aliyuncs.com"]
}
EOF

sudo systemctl daemon-reload

sudo systemctl restart docker
```

## 回顾hello-world了解Docker运行原理

![image-20201119125135947](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225701.png)

## 底层原理

### 1.Docker是怎么工作的？

Docker是一个Client-Server结构的系统，Docker的守护进程运行在服务器上。通过Socket客户端访问！

![image-20201119125148203](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225702.png)

# Docker命令



## 帮助命令

### docker version 

#显示Docker版本信息

```shell
[root@localhost ~]# docker version
Client: Docker Engine - Community
 Version:           19.03.13
 API version:       1.40
 Go version:        go1.13.15
 Git commit:        4484c46d9d
 Built:             Wed Sep 16 17:03:45 2020
 OS/Arch:           linux/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          19.03.13
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.13.15
  Git commit:       4484c46d9d
  Built:            Wed Sep 16 17:02:21 2020
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.3.7
  GitCommit:        8fba4e9a7d01810a393d5d25a3621dc101981175
 runc:
  Version:          1.0.0-rc10
  GitCommit:        dc9208a3303feef5b3839f4323d9beb36df0a9dd
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683
[root@localhost ~]#
```

### docker info  

#显示docker的系统信息，包括镜像和容器的数量。

```shell
[root@localhost ~]# docker info
Client:
 Debug Mode: false

Server:
 Containers: 1
  Running: 0
  Paused: 0
  Stopped: 1
 Images: 1
 Server Version: 19.03.13
 Storage Driver: overlay2
  Backing Filesystem: xfs
  Supports d_type: true
  Native Overlay Diff: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 8fba4e9a7d01810a393d5d25a3621dc101981175
 runc version: dc9208a3303feef5b3839f4323d9beb36df0a9dd
 init version: fec3683
 Security Options:
  seccomp
   Profile: default
 Kernel Version: 3.10.0-1127.19.1.el7.x86_64
 Operating System: CentOS Linux 7 (Core)
 OSType: linux
 Architecture: x86_64
 CPUs: 1
 Total Memory: 1.777GiB
 Name: localhost.localdomain
 ID: 4ARA:NX4Y:7DM7:IGVR:XQNU:PNSQ:SDFN:44U2:VINY:2OMR:VDKO:2SKU
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Registry Mirrors:
  https://gnxq79wc.mirror.aliyuncs.com/
 Live Restore Enabled: false

[root@localhost ~]#
```

### docker 命令 --help    

#帮助命令

https://docs.docker.com/

![image-20201119130056882](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225703.png)

![image-20201119130250304](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225704.png)

命令：https://docs.docker.com/engine/reference/commandline/

## 镜像命令

### docker images

查看所有本地主机上的镜像

![image-20201119130348269](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225705.png)

```shell
[root@localhost ~]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              bf756fb1ae65        10 months ago       13.3kB

#解释
REPOSITORY  镜像仓库源
TAG			镜像的标签
IMAGE ID	镜像的ID
CREATED		镜像的创建时间
SIZE		镜像的大小
```

### Options选项

```shell
[root@localhost ~]# docker images --help

Usage:	docker images [OPTIONS] [REPOSITORY[:TAG]]

List images

Options:
  -a, --all             Show all images (default hides intermediate images)
      --digests         Show digests  #格式化
  -f, --filter filter   Filter output based on conditions provided  #过滤
      --format string   Pretty-print images using a Go template
      --no-trunc        Don't truncate output
  -q, --quiet           Only show numeric IDs

```

#解释

-a		列出所有镜像

-q		只显示镜像的ID

```shell
[root@localhost ~]# docker images -a
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              bf756fb1ae65        10 months ago       13.3kB
[root@localhost ~]# docker images -aq
bf756fb1ae65
[root@localhost ~]#
```

## 搜索命令

### 网页搜索

https://hub.docker.com/

![image-20201119143850428](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225706.png)

### docker search

docker search --help

```shell
[root@localhost ~]# docker search --help

Usage:	docker search [OPTIONS] TERM

Search the Docker Hub for images

Options:
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print search using a Go template
      --limit int       Max number of search results (default 25)
      --no-trunc        Don't truncate output
[root@localhost ~]#
```

例如：

--filter=STARS=3000  #过滤出镜像收藏大于3000的

```shell
[root@localhost ~]# docker search mysql --filter=STARS=3000
NAME                DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
mysql               MySQL is a widely used, open-source relation…   10115               [OK]                
mariadb             MariaDB is a community-developed fork of MyS…   3715                [OK]                
[root@localhost ~]#
```

## 下载命令

### docker pull

```shell
[root@localhost ~]# docker pull --help

Usage:	docker pull [OPTIONS] NAME[:TAG|@DIGEST]

Pull an image or a repository from a registry

Options:
  -a, --all-tags                Download all tagged images in the repository
      --disable-content-trust   Skip image verification (default true)
      --platform string         Set platform if server is multi-platform capable
  -q, --quiet                   Suppress verbose output
[root@localhost ~]#
```



```shell

[root@localhost ~]# docker pull mysql
Using default tag: latest   #如果不写tag:，默认下载最新的版本
latest: Pulling from library/mysql
bb79b6b2107f: Pull complete    #分层下载，docker image的核心：联合文件系统
49e22f6fb9f7: Pull complete 
842b1255668c: Pull complete 
9f48d1f43000: Pull complete 
c693f0615bce: Pull complete 
8a621b9dbed2: Pull complete 
0807d32aef13: Pull complete 
a56aca0feb17: Pull complete 
de9d45fd0f07: Pull complete 
1d68a49161cc: Pull complete 
d16d318b774e: Pull complete 
49e112c55976: Pull complete 
Digest: sha256:8c17271df53ee3b843d6e16d46cff13f22c9c04d6982eb15a9a47bd5c9ac7e2d   #签名
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest   #真实地址
[root@localhost ~]
```

docker pull mysql=docker pull docker.io/library/mysql:latest   #等价

### 指定下载版本

docker pull 镜像名:tag

注：指定下载的版本必须是存在的。

联合文件系统，公用文件不在下载极大减少占用存储

比较：

```shell
[root@localhost ~]# docker pull mysql
Using default tag: latest
latest: Pulling from library/mysql
bb79b6b2107f: Pull complete 
49e22f6fb9f7: Pull complete 
842b1255668c: Pull complete 
9f48d1f43000: Pull complete 
c693f0615bce: Pull complete 
8a621b9dbed2: Pull complete 
0807d32aef13: Pull complete 
a56aca0feb17: Pull complete 
de9d45fd0f07: Pull complete 
1d68a49161cc: Pull complete 
d16d318b774e: Pull complete 
49e112c55976: Pull complete 
Digest: sha256:8c17271df53ee3b843d6e16d46cff13f22c9c04d6982eb15a9a47bd5c9ac7e2d
Status: Downloaded newer image for mysql:latest
docker.io/library/mysql:latest
[root@localhost ~]# docker pull mysql:5.7
5.7: Pulling from library/mysql
bb79b6b2107f: Already exists 
49e22f6fb9f7: Already exists 
842b1255668c: Already exists 
9f48d1f43000: Already exists 
c693f0615bce: Already exists 
8a621b9dbed2: Already exists 
0807d32aef13: Already exists 
f15d42f48bd9: Pull complete 
098ceecc0c8d: Pull complete 
b6fead9737bc: Pull complete 
351d223d3d76: Pull complete 
Digest: sha256:4d2b34e99c14edb99cdd95ddad4d9aa7ea3f2c4405ff0c3509a29dc40bcb10ef
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7
[root@localhost ~]#
```

查看下载的镜像

![image-20201119143955130](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225707.png)

## 删除镜像命令

### docker rmi -f id

docker rmi -f  id1 id2 id3   #删除多个指定的容器镜像

通过ID删除镜像/通过TAG删除镜像

![image-20201119144041725](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225708.png)

再次查看，mysql 5.7已被删除，只删除了部分层。

![image-20201119144111592](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225709.png)

### 删除全部容器镜像

```
docker rmi -f $(docker images -aq)
```

![image-20201119144145180](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225710.png)

# 容器命令

有了镜像才可以创建容器，下载一个centos镜像来测试学习

## 下载镜像

```shell
docker pull centos
```

![image-20201119154921147](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225711.png)

## 新建容器并启动

```shell
docker run [可选参数] image
```

#参数说明

--name='Name'		容器名字，用来区分容器

-d								后台方式运行

-it								使用交互方式运行，进入容器查看内容

-p								指定容器的端口 -p 8080:8080

​		-p  主机端口映射：容器端口（常用）	

​		-p  直接容器端口

-P								随机指定端口（大写）

查看docker run帮助命令

```shell
docker run --help
```

查看下载的镜像

```shell
docker images
```

测试启动并进入容器

```shell
docker run -it centos /bin/bash
#主机名称变更
cd /
ls
查看容器内的centos
从容器中退回主机
exit   #直接停止并退出
```

![image-20201119155032132](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225712.png)

## 列出运行正在的容器

```shell
docker ps
```

![image-20201119155047435](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225713.png)

列出所有运行过的容器

```shell
docker ps -a
```

![image-20201119155128978](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225714.png)

显示最近创建的容器

```shell
docker ps -a -n=1
```

![image-20201119155231771](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225715.png)

显示所有运行容器的编号

```shell
docker ps -aq
```

![image-20201119155246267](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225716.png)

## 退出容器

exit

直接停止并退出

Ctrl+P+Q

容器不停止退出

![image-20201119155321420](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225717.png)

## 删除容器镜像

```shell
docker rm ID   #删除指定的容器镜像，不能删除正在运行的容器镜像
```

```shell
docker rm -f $(docker ps -aq)   #删除所有的容器镜像
```

```shell
docker ps -a -q|xargs docker rm -f   #删除所有的容器镜像
```

![image-20201119155409896](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225718.png)

centos8报错

![image-20201119155507959](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225719.png)

## 启动停止容器

启动

```shell
docker start ID
```

重启

```shell
docker restart ID
```

停止当前正在运行容器

```shell
docker stop ID
```

强制停止当前运行容器

```shell
docker kill ID
```

## 后台启动

docker run -d 镜像名

问题：

1.Docker容器使用后台运行，就必须要有一个前台进程，Docker发现没有前台应用，就会自动停止

2.例：nginx,容器启动后，发现自己没有提供服务，就会立刻停止，就是没有程序了

![image-20201119155545647](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225720.png)

## 查看日志

```shell
docker logs
```

查看帮助命令

```shell
docker logs --help
```

![image-20201119155622025](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225721.png)

首先启动容器镜像

docker run -it centos /bin/bash

写一点脚本

docker run -d centos /bin/sh -c "while true;do echo test;sleep 1;done"

查看日志

```shell
docker logs -tf ID
```

查看具体行的日志

```shell
docker logs -tf --tail N ID
```

![image-20201119155753931](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225722.png)

## 进程信息

### docker top ID

```shell
docker top ID
```

![image-20201119155838490](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225723.png)

## 容器信息

```shell
docker inspect ID
```

帮助命令

![image-20201119155848170](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225724.png)

![image-20201119155925402](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225725.png)

Args:传递的参数

pid:进程

![image-20201119160014717](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225726.png)

Mounts:挂载信息

Env:环境变量

![image-20201119160118447](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225727.png)

```shell
[root@localhost ~]# docker inspect 072d6fb47015
[
    {
        "Id": "072d6fb47015c713a12a27f9dd9b52d140260fadc320c50415656f1547d3b056",
        "Created": "2020-11-02T04:44:44.123849543Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 2448,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2020-11-02T04:44:44.305600406Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:0d120b6ccaa8c5e149176798b3501d4dd1885f961922497cd0abef155c869566",
        "ResolvConfPath": "/var/lib/docker/containers/072d6fb47015c713a12a27f9dd9b52d140260fadc320c50415656f1547d3b056/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/072d6fb47015c713a12a27f9dd9b52d140260fadc320c50415656f1547d3b056/hostname",
        "HostsPath": "/var/lib/docker/containers/072d6fb47015c713a12a27f9dd9b52d140260fadc320c50415656f1547d3b056/hosts",
        "LogPath": "/var/lib/docker/containers/072d6fb47015c713a12a27f9dd9b52d140260fadc320c50415656f1547d3b056/072d6fb47015c713a12a27f9dd9b52d140260fadc320c50415656f1547d3b056-json.log",
        "Name": "/wonderful_carson",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Capabilities": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/31c0a7dadc6ab0aac8610ef1cbc6453a7deb07b7e4041eb13d0fde9ffcc1fca2-init/diff:/var/lib/docker/overlay2/a3eea815ce2e49aeb13672555a2278994bc4d4510b0e7d8418f5966573d90b7b/diff",
                "MergedDir": "/var/lib/docker/overlay2/31c0a7dadc6ab0aac8610ef1cbc6453a7deb07b7e4041eb13d0fde9ffcc1fca2/merged",
                "UpperDir": "/var/lib/docker/overlay2/31c0a7dadc6ab0aac8610ef1cbc6453a7deb07b7e4041eb13d0fde9ffcc1fca2/diff",
                "WorkDir": "/var/lib/docker/overlay2/31c0a7dadc6ab0aac8610ef1cbc6453a7deb07b7e4041eb13d0fde9ffcc1fca2/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "072d6fb47015",
            "Domainname": "",
            "User": "",
            "AttachStdin": true,
            "AttachStdout": true,
            "AttachStderr": true,
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": true,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "centos",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20200809",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS"
            }
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "8b6a572d50123d07c047632ddc336df8a9f717e485a09e5b469d572a435514ce",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/8b6a572d5012",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "c75a2ed0b7f7a7de7315f9c0ce8d1a77324949ae192f5ca4d8a0040ec1581738",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "697346d198aa6d39088da36bf3aa32eee7ef70ae170fa52118cb7ed8cc8993f6",
                    "EndpointID": "c75a2ed0b7f7a7de7315f9c0ce8d1a77324949ae192f5ca4d8a0040ec1581738",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
[root@localhost ~]# 
```

## 进入运行容器

通常容器都是使用后台方式运行，需要进入容器，修改一些配置

### docker exec

```shell
docker exec -it 容器ID bashshell
```

测试

```shell
[root@localhost ~]# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
072d6fb47015        centos              "/bin/bash"         6 hours ago         Up 6 hours                              wonderful_carson
[root@localhost ~]# docker exec -it 072d6fb47015 /bin/bash
[root@072d6fb47015 /]# ls
bin  etc   lib	  lost+found  mnt  proc  run   srv  tmp  var
dev  home  lib64  media       opt  root  sbin  sys  usr
[root@072d6fb47015 /]# ps -ef
UID         PID   PPID  C STIME TTY          TIME CMD
root          1      0  0 05:52 pts/0    00:00:00 /bin/bash
root         16      0  0 10:25 pts/1    00:00:00 /bin/bash
root         30     16  0 10:26 pts/1    00:00:00 ps -ef
[root@072d6fb47015 /]#
```

![image-20201119160149309](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225728.png)

### docker attach

```shell
docker attach 容器ID
```

比较:

docker exec		进入容器后开启一个新的终端，可以在里面操作（常用）

docker attach		进入容器正在执行的终端，不会启动新的进程！

## 从容器内拷贝文件到主机

### docker cp

```shell
docker cp 容器ID:容器内路径 主机路径
```

```shell
[root@localhost ~]# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
072d6fb47015        centos              "/bin/bash"         6 hours ago         Up 6 hours                              wonderful_carson
#进入docker容器内部
[root@localhost ~]# docker attach 072d6fb47015
[root@072d6fb47015 /]# cd /home/
[root@072d6fb47015 home]# ls
#在容器内新建一个文件
[root@072d6fb47015 home]# touch test.txt
[root@072d6fb47015 home]# ls
test.txt
#退出容器进行拷贝测试，退出不影响文件的拷贝
[root@072d6fb47015 home]# exit
exit
#将文件拷贝到主机上
[root@localhost ~]# docker cp 072d6fb47015:/home/test.txt /home/
[root@localhost ~]# cd /home/
[root@localhost home]# ls
test.txt
[root@localhost home]#
```

![image-20201119160242014](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225729.png)

小结

![image-20201119160339372](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225730.png)

attach	 	Attach to a running container 	#当前she 11  下attach连接指定运行镜像 

build 		Bui1dan image from a Docker file 		#通过Docker file定制镜像 

commit		 Create a new image from a container changes		 #提交当前容器为新的镜像 

cp		 Copyfiles/fo1ders from the containers filesystem to the host path		 #从容器中拷贝指定文件或者目录到宿主机中 

create		 Create a new container		 #创建一个新的容器， 同run， 但不启动容器 

diff		 Inspect changes on a container's filesystem 			#查看docker容器变化 

events		 Get real time events from the server 		#从docker服务获取容器实时事件 

exec		 Run a command in an existing container 		#在已存在的容器上运行命令 

export 		Stream the contents of a container as at ar archive 		#导出容器的内容流作为一个tar归档文件[对应 import] 

history		 show the history of an image 		#展示一个镜像形成历史 

images		 List images 		#列出系统当前镜像 

import		 create a new filesystem image from the contents of at arba 11		#从tar包中的内容创建一个新的文件系 统映像[对应export] 

info		 Display system-wide information 		#显示系统相关信息

inspect		 Return 1ow-1eve 1 information on a container 		#查看容器详细信息 

kill		 kill a running container 		#ki ll指定docker容器 

load 		Load an image from at ar archive		 #从一个tar包中加载一个镜像[对应save] 

login 		Register or Login to the docker registry server		 #注册或者登陆一个docker源服务器

logout 		Logout from a Docker registry server 		#从当前Docker registry退出 

logs 		Fetch the 1ogsofa container 		#输出当前容器日志信息 

port		 Lookup the pub1ic-facing port which is NAT-ed to PRIVATE_PORT 		#查看映射端口对应的容器内部源端 口 

pause		 Pause a 11  processes within a container 		#暂停容器 

ps		 List containers 		#列出容器列表 

pull		 Pullanimageora repository from the docker registry server 		#从docker镜像源服务器拉取指定镜像或者库镜像 

push		 Push an image or a repository to the docker registry server 		#推送指定镜像或者库镜像至docker源服务器 

restart		 Restart a running container 		#重启运行的容器 

rm		 Remove one or more containers 		#移除一个或者多个容器 

rmi		 Remove one or more images 		#移除一个或多个镜像[无容器使用该镜像才可删除，否则需删除相关容 器才可继续或-f强制删除] 

run		 Run a command in a new container		 #创建一个新的容器并运行一个命令 

save		 Save an image to at ar archive 		#保存一个镜像为一个tar包[对应1oad] 

search		 Search for an image on the Docker Hub 		#在docker hub中搜索镜像 

start		 Start a stopped containers 		#启动容器

stop		 Stop a running containers 		#停止容器

 tag		 Tagan image into a repository		 #给源中镜像打标签 

top		 Lookup the running processes of a container 		#查看容器中运行的进程信息

 un pause 		Un pause a paused container 		#取消暂停容器 

version		 Show the docker version information 		#查看docker版本号 

wait		 Block until a container stops， then print its exitcode 		#截取容器停止时的退出状态值 

# 部署Nginx

## 搜索镜像

网页搜索镜像

建议在docker hub进行搜索，可以看到帮助文档。

![image-20201119195905002](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225731.png)

打开查看镜像详细信息

命令搜索镜像

```shell
docker search nginx
```

![image-20201119195951827](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225732.png)

## 下载镜像

```shell
docker pull nginx
```

![image-20201119200059004](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225733.png)

## 查看下载的镜像

```shell
docker images
```

![image-20201119200141880](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225734.png)

## 启动镜像

```shell
docker run -d --name=nginx01 -p 3344:80 nginx
```

-d		#后台运行

--name		#给容器起名

-p		#暴露端口（宿主机端口：容器内部端口）

![image-20201119200223739](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225735.png)

## 查看运行容器

```
docker ps
```

![image-20201119200304871](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225736.png)

## 请求测试

```shell
curl localhost:3344
```

![image-20201119200345627](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225737.png)

![image-20201119200416380](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225738.png)

## 进入容器

```shell
docker exec -it nginx01 /bin/bash
```

进入容器，搜索nginx,查看nginx配置文件，退出容器，停止容器，再次访问测试

```shell
[root@localhost ~]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STAT
370ce844910c        nginx               "/docker-entrypoint.…"   17 minutes ago      Up 1
[root@localhost ~]# docker exec -it nginx01 /bin/bash
root@370ce844910c:/# whereis nginx
nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx
root@370ce844910c:/# cd /etc/nginx/
root@370ce844910c:/etc/nginx# ls
conf.d		koi-utf  mime.types  nginx.conf   uwsgi_params
fastcgi_params	koi-win  modules     scgi_params  win-utf
root@370ce844910c:/etc/nginx# exit
exit
[root@localhost ~]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
370ce844910c        nginx               "/docker-entrypoint.…"   19 minutes ago      Up 19 minutes       0.0.0.0:3344->80/tcp   nginx01
[root@localhost ~]# docker stop 370ce844910c
370ce844910c
[root@localhost ~]#
```

停止容器后便无法访问nginx

![image-20201119200512408](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225739.png)

# 部署tomcat

## 搜索镜像

![image-20201119200944782](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225740.png)

官方使用：

![image-20201119201055101](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225741.png)

测试使用：用完即删除容器

```shell
docker run -it --rm toncat:9.0
```

![image-20201119201208092](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225742.png)

容器删除，镜像还在

![image-20201119201249992](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225743.png)

## 下载镜像

```shell
docker pull tomcat
```

## 查看下载的镜像

```shell
docker images
```

## 启动镜像

以后台的方式启动

```shell
docker run -d -p 3355:8080 --name=tomcat01 tomcat
```

![image-20201119201400744](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225744.png)

## 访问测试

测试访问没有问题，少东西

![image-20201119201443336](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225745.png)

## 进入容器

```shell
docker exec -it tomcat01 /bin/bash
```

问题：

命令缺少

webapps目录没有文件

原因：

阿里云镜像原因，默认最小的镜像，

所有不必要的都删除掉，保证最小可运行的环境。

![image-20201119201522330](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225746.png)

## 解决访问

webapps文件被放在了webapps.dist目录中，拷贝webapps.dist目录下的所有文件到webapps中，再次刷新测试访问。

![image-20201119201557374](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225747.png)

再次测试

![image-20201119201636512](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225748.png)

# 部署es+kibana

全文搜索引擎elasticsearch

## 搜索镜像

![image-20201119204453299](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225749.png)

es:

暴露的端口很多

十分的耗内存

--net somenetwork  网络

## 下载启动镜像

```shell
docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.6.2
```

![image-20201119204538602](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225750.png)

## 查看运行容器

```shell
docker ps
```

![image-20201119204630918](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225751.png)

## 查看CPU内存状态

内存占用较高

```shell
docker stats
```

![image-20201119204710675](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225752.png)

## 请求测试

```shell
curl localhost:9200
```

![image-20201119204800920](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225753.png)

## 增加内存限制

关闭容器，增加内存限制，修改配置文件 

-e:环境配置修改

```shell
docker ps
docker stop ID
```

![image-20201119204842838](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225754.png)

修改配置再次启动

```shell
docker run -d --name elasticsearch02 -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx512m" elasticsearch:7.6.2
```

![image-20201119204930987](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225755.png)

## 再次查看状态

![image-20201119205016299](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225756.png)

## 请求测试

```shell
curl localhost:9200
```

![image-20201119205104377](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225757.png)



## 使用kibana连接elasticsearch

![image-20201119205212970](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225758.png)

## portainer可视化

Docker图形化界面管理工具！提供一个后台面板供我们操作！

## 下载运行镜像

```shell
docker run -d -p 8088:9000 \
--restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer
```

![image-20201119205251498](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225759.png)

## 访问测试

```shell
curl localhost:8088
```

![image-20201119205347438](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225800.png)

## 网页访问

```
http://IP:8088
```

![image-20201119205427904](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225801.png)

设置密码，创建用户。选择LOCAL数据。

![image-20201119205511152](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225802.png)

![image-20201119205600299](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225803.png)

## 进入面板

![image-20201119205639509](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225804.png)

# Docker镜像讲解

## 镜像是什么？

镜像是一种轻量级、可执行的独立软件包，用来打包软件运行环境和基于运行环境开发的软件，它包含运行某个软件所需的所有内容，包括代码、运行时、库、环境变量和配置文件。 

所有的应用， 直接打包成docker镜像， 就可以直接跑起来! 

## 如何得到镜像？

从远程仓库下载 

朋友拷贝给你

自己制作一个镜像Docker File

##  UnionFS联合文件系统

我们下载的时候看到的一层一层就是分层下载！

UnionFS(联合文件系统) ：Union文件系统(UnionFS) 是一种分层、轻量级并且高性能的文件系统， 它支持对文件系统的修改作为一次提交来一层层的叠加，同时可以将不同目录挂载到同一个虚拟文件系统下(unite several directories into a single virtual filesystem) 。Union文件系统是Docker镜像的基础。镜像可以通过分层来进行继承， 基于基础镜像(没有父镜像) ， 可以制作各种具体的应用镜像。 

特性：一次同时加载多个文件系统，但从外面看起来，只能看到一个文件系统，联合加载会把各层文件系统叠加起来，这样最终的 文件系统会包含所有底层的文件和目录 。

## Docker镜像加载原理

docker的镜像实际上由一层一层的文件系统组成， 这种层级的文件系统UnionFS。 

bootfs(boot file system) 主要包含bootloader和kernel，bootloader主要是引导加载kernel， Linux刚启动时会加载bootfs文件系统，在Docker镜像的最底层是bootfs。这一层与我们典型的Linux/Unix系统是一样的， 包含boot加载器和内核。当boot加载完成之后整个内核就都在内存中了， 此时内存的使用权已由bootfs转交给内核， 此时系统也会卸载bootfs。 

rootfs(root file system) ，在bootfs之上。包含的就是典型Linux系统中的/dev，/proc，/bin，/etc等标准目录和文件。rootfs就是各种不同的操作系统发行版， 比如Ubuntu， Centos等等。

![image-20201119210544013](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225805.png)

平时我们安装进虚拟机的CentOS都是好几个G， 为什么Docker这里才200M? 

![image-20201119210643165](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225806.png)

对于一个精简的OS,rootfs可以很小，只需要包含最基本的命令,工具和程序库就可以了， 因为底层直接用Host的kernel， 自己只需要提供rootfs就可以了。由此可见对于不同的linux发行版， bootfs基本是一致的,rootfs会有差别,因此不同的发行版可以公用 bootfs。 

底层引导不变

虚拟机分钟级别，容器秒级。

## 分层的镜像

我们可以去下载一个镜像，注意观察下载的日志输出，可以看到是一层一层的在下载! 

![image-20201119210715789](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225807.png)

思考：为什么Docker镜像要采用这种分层的结构呢? 

最大的好处，莫过于是资源共享!比如有多个镜像都从相同的Base镜像构建而来,那么宿主机只需在磁盘上保留一份base镜像,同时内存中也只需要加载一份base镜像,这样就可以为所有的容器服务了, 而且镜像的每一层都可以被共享。

 查看镜像分层的方式可以通过docker image inspect命令!

```shell
[root@localhost ~]# docker image inspect redis:latest
[
    //......
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:d0fe97fa8b8cefdffcef1d62b65aba51a6c87b6679628a2b50fc6a7a579f764c",
                "sha256:832f21763c8e6b070314e619ebb9ba62f815580da6d0eaec8a1b080bd01575f7",
                "sha256:223b15010c47044b6bab9611c7a322e8da7660a8268949e18edde9c6e3ea3700",
                "sha256:6a9976a8f40851f45dc8c68a04b130e90522f46bb7e8403c6e7eb4331674f213",
                "sha256:c875a9fc3ec72b140e325e1a1b3b57d299b91811e8288a07c6b788b0d7cba185",
                "sha256:d9364cb75b1a364fbcb97b2f51332fc012ae0321e18c3fd3811f5e5a9f8a2d0e"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]

```

理解：

所有的Docker镜像都起始于一个基础镜像层，当进行修改或增加新的内容时，就会在当前镜像层之上创建新的镜像层。举一个简单的例子，假如基于Ubuntu Linux 16.04创建一个新的镜像，这就是新镜像的第一层；如果在该镜像中添加Python包就会在基础镜像层之上创建第二个镜像层；如果继续添加一个安全补丁，就会创建第三个镜像层。该镜像当前已经包含3个镜像层，如下图所示(这只是一个用于演示的很简单的例子)。 

![image-20201119210811630](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225808.png)

在添加额外的镜像层的同时，镜像始终保持是当前所有镜像的组合，理解这一点非常重要。下图中举了一个简单的例子，每个镜像层包含3个文件，而镜像包含了来自两个镜像层的6个文件。 

![image-20201119210910589](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225809.png)

上图中的镜像层跟之前图中的略有区别，主要目的是便于展示文件。 下图中展示了一个稍微复杂的三层镜像，在外部看来整个镜像只有6个文件，这是因为最上层中的文件7是文件5的一个更新版本。 

![image-20201119210950061](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225810.png)

这种情况下，上层镜像层中的文件覆盖了底层镜像层中的文件。这样就使得文件的更新版本作为一个新镜像层添加到镜像当中。 Docker通过存储引擎(新版本采用快照机制) 的方式来实现镜像层堆栈， 并保证多镜像层对外展示为统一的文件系统。 Linux上可用的存储引擎有AUFS、 Overlay2、Device Mapper、Btrfs以及ZFS。顾名思义， 每种存储引擎都基于Linux中对应的文件系统或者块设备技术，并且每种存储引擎都有其独有的性能特点。 Docker在Windows上仅支持windows filter一种存储引擎， 该引擎基于NTFS文件系统之上实现了分层和CoW[1] 。 下图展示了与系统显示相同的三层镜像。所有镜像层堆叠并合并，对外提供统一的视图。 

![image-20201119211033079](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225811.png)

## 特点

Docker镜像都是只读的， 当容器启动时， 一个新的可写层被加载到镜像的顶部 这一层就是我们通常说的容器层，容器之下的都叫镜像层! 

![image-20201119211112042](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225812.png)

注：所有的操作都是基于容器层。

如何提交一个自己的镜像？

# commit提交镜像

提交修改的容器成为一个新的副本

```shell
docker commit
```

```shell
docker commit -m="提交的描述信息" -a="作者" ID目标镜像名:[TAG]
```

## 查看镜像

```shell
docker images
```

![image-20201120120426104](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225813.png)

## 交互模式启动

```
docker run -it -p 8080:8080 tomcat
```

![image-20201120120534550](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225814.png)

新开窗口

## 查看运行容器

```shell
docker ps
```

![image-20201120120609122](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225815.png)

## 进入运行的容器

```shell
docker exec -it ID /bin/bash
```

## 修改容器内容

启动默认的tamcat

发现这个默认的tamcat是没有webapps应用，镜像的原因，官方镜像默认webapps下面是没有文件的。

自己拷贝进去基本文件

![image-20201120120707713](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225816.png)

## 将修改的容器打包

```shell
docker commit -m="提交的描述信息" -a="作者" ID 目标镜像名:[TAG版本]
```

-a="作者"

-m="描述"

```shell
docker commit -a="lwenwu" -m="add webapps app" 444facacd961 tomcat02:1.0
```

![image-20201120120746550](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225817.png)

## 查看打包好的镜像

```shell
docker images
```

![image-20201120120830068](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225818.png)

比原来的镜像大了一些，可以直接启动运行。

# 容器数据卷

什么是容器数据卷？

 docker的理念回顾

 将应用和环境打包成一个镜像!

 数据?如果数据都在容器中，那么我们容器删除，数据就会丢失!需求：数据可以持久化 

MySQL，容器删了，删库跑路!需求：MySQL数据可以存储在本地!

容器之间可以有一个数据共享的技术!Docker容器中产生的数据，同步到本地!这就是卷技术!目录的挂载，将我们容器内的目录，挂载到Linux上面! 

![image-20201120121542397](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225819.png)

总结一句话：容器的持久化和同步操作！容器间也是可以数据卷共享的！

## 使用数据卷

## 使用命令挂载

-v

```shell
docker run -it -v 主机目录：容器目录
```

```shell
docker run -it -v /home/test:/home centos /bin/bash
```





## 查看容器挂载信息

新开窗口，在主机目录下查看

```shell
docker inspect ID
```

![image-20201120121641921](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225820.png)

## 测试文件同步

双向绑定，自动同步。

![image-20201120121723621](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225821.png)

容器删除，数据不会丢失。

## 双向测试

容器退出，宿主机上修改文件测试同步

```shell
exit
```

宿主机上修改完文件后，开启容器，进入容器

```shell
docker start ID
```

```shell
docker attach ID
```

进入目录，查看数据。

![image-20201120121815350](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225822.png)

# 实战MySQL

## 搜索镜像

```shell
docker search mysql
```

![image-20201120122248502](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225823.png)

## 下载镜像

```shell
docker pull mysql:5.7
```

## 查看下载的镜像

![image-20201120122515908](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225824.png)

## 启动容器

安装启动mysql,需要设置密码。

官方说明：

![image-20201120122556726](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225825.png)

后台运行

```shell
docker run -d -p 3310:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql --name mysql01 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
```

![image-20201120122640164](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225826.png)

-d:后台运行

-p:端口映射

-v:数据卷挂载

-e:环境配置

--name:容器名称

## 连接测试

启动成功，我们在本地使用sqlyog进行测试,新建连接。

sqlyog-连接到服务器的3310----3310和容器内的3306映射，这个时候我们就可以连接上了!

![image-20201120122732913](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225827.png)

![image-20201120122815271](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225828.png)

## 宿主机确认目录

![image-20201120122855573](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225829.png)

## sqlyog上创建数据库测试

![image-20201120122931955](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225830.png)

## 创建test数据库

![image-20201120123006207](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225831.png)

![image-20201120123158307](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225832.png)

## 主机测试传输

查看映射的数据是否OK!

![image-20201120123232513](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225833.png)

## 配置本地修改

容器中MySQL配置直接在本地/home/conf下进行配置，配置前应先将容器中的配置拷贝到主机配置目录。

![image-20201120123316274](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225834.png)

## 删除测试

删除容器，容器数据丢失，查看本地数据。

```shell
docker rm -f mysql01
```

![image-20201128121130323](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225835.png)

查看运行的容器

```shell
docker ps
```

已经没有mysql01容器

![image-20201120123409244](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225836.png)

发现，我们挂载到本地的数据卷依旧没有丢失，这就实现了容器数据持久化功能! 

![image-20201120123559241](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225837.png)

# 具名、匿名、指定路径挂载

## 匿名挂载

-v 直接指定容器内路径

```shell
docker run -d -P --name nginx01 -v /etc/nginx nginx
```

![image-20201120124223490](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225838.png)

### 查看卷帮助信息

```shell
docker volume --help
```

![image-20201120124257618](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225839.png)

### 查看所有卷

volume name为随机数字

ac173af98840fdb2c146eada65ebb0de10c9b402b4701e76a7f52fd83bf1556b

e831e07007d636fef22472ca81d64eccbdc5e1dab6d550e15d39b84a2e30988f

![image-20201120124409762](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225840.png)



## 具名挂载

### 命令卷

通过 -v   卷名：容器内路径

```shell
docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx nginx
```

![image-20201120124602617](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225841.png)

### 查看所有卷

```shell
docker volume ls
```

![image-20201120124637702](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225842.png)

### 查看卷位置

```shell
docker volume inspect juming-nginx
```

![image-20201120124716387](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225843.png)

### 进入卷

![image-20201120124752040](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225844.png)

所有的docker容器内的卷，没有指定目录的情况下都是在 /var/lib/docker/volumes/xxxx/_data

我们通过具名挂载可以方便的找到我们的一个卷，大多数情况使用具名挂载。

如何确定是具名挂载还是匿名挂载，还是指定路径挂载？

-v  容器内路径 								#匿名挂载 

-v  卷名：容器内路径 					#具名挂载 

-v 主机路径:容器内路径				#指定路径挂载

拓展：

\#通过-v容器内路径：ro/rw 可改变读写权限

 ro 	readonly 	#只读 

rw	readwrite 	#可读可写 

\#一旦这个设置了容器权限，容器对我们挂载出来的内容就有限定了! 

```shell
docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx:ro nginx
docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx:rw nginx
```

\#ro  只要看到ro就说明这个路径只能通过宿主机来操作，容器内部是无法操作的! 

## 指定路径挂载

-v 主机路径:容器内路径				#指定路径挂载

# DockerFile

## DockerFile制作镜像

进入/home

创建docker-test-volume目录

进入docker-test-volume目录，创建dockerfile文件（名字可随意，建议用dockerfile）

文件中的内容：

指令都大写，参数小写

```
FROM centos

VOLUME ["volume01","volume02"]

CMD echo "-----------end------------"

CMD /bin/bash
```

每个命令，就相当于镜像的一层。

## 构建镜像

build 	构建

-f			脚本文件地址

-t			生产 文件名

最后需要.点

```
docker build -f /home/docker-test-volume/dockerfile1 -t lwemwu/centos .
```

分层构建

![image-20201123121811829](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225845.png)

## 查看镜像

```
docker images
```

![image-20201123121859213](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225846.png)

## 启动镜像

```
docker run -it ID /bin/bash
```

这个目录就是我们生成镜像的时候自动挂载的数据卷目录。

这个卷和外部一定有一个同步的目录。

![image-20201123121930917](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225847.png)

## 容器内部创建文件

外部一定有一个同步的目录。

![image-20201123122004492](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225848.png)

退出容器

## 宿主机查看

查看运行容器

```
docker ps -a
```

查看容器详细信息

```
docker inspect id
```

![image-20201128121058588](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225849.png)

进入挂载路径，查看本地数据是否被同步过来。

![image-20201123122117640](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225850.png)

测试一下刚才的文件是否同步出去了!

 这种方式我们未来使用的十分多，因为我们通常会构建自己的镜像! 

假设构建镜像时候没有挂载卷，要手动镜像挂载-v卷名：容器内路径!| 

# 数据卷容器

容器间数据同步

![image-20201124121246456](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225851.png)

启动3个容器，通过我们刚才自己构建的镜像启动。

## 查看容器

```
docker images
```

![image-20201124121257866](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225852.png)

## 启动Docker01

```
docker run -it --name docker01 lwemwu/centos
```

![image-20201124121323322](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225853.png)

Ctrl+P+Q退出容器

继续运行

![image-20201124121358026](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225854.png)

## 启动Docker02

```
docker run -it --name docker02 --volumes-from docker01 lwemwu/centos
```

![image-20201124121458489](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225855.png)

## 测试同步

在Docker01中增加文件docker01,到Docker02查看数据同步。

```
docker attach docker01(ID)
```

![image-20201124121519808](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225856.png)

进入docker02查看。

![image-20201124121548632](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225857.png)

docker01创建的文件在docker02上同步了过来。

## 启动Docker03

```
docker run -it --name docker03 --volumes-from docker01 lwemwu/centos
```

![image-20201124121620134](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225858.png)

到docker02查看volume01数据。

![image-20201124121650291](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225859.png)

总结：通过--volumes-from可以实现容器间的数据共享。

## 删除容器测试数据

```
docker ps -a
```

![image-20201124121750827](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225900.png)

删除容器

```
docker rm -f ID
```

![image-20201124121820841](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225901.png)

docker01已被删除

![image-20201124121847513](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225902.png)

进入docker02、docker01查看数据是否还在？

数据未丢失，可以访问。

![image-20201128121005637](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225903.png)

## 多个mysql数据同步

```
docker run -d -p 3310:3306 -v /etc/mysql/conf.d -v var/lib/mysql --name mysql01 -e MYSQL_ROOT_PASSWORD=123456 mysql:5.7

docker run -d -p 3310:3306 -e MYSQL_ROOT_PASSWORD=123456 --name mysql02 --volumes-from mysql01 mysql:5.7

实现容器数据同步
```

结论： 

容器之间配置信息的传递，数据卷容器的生命周期一直持续到没有容器使用为止。 

但是一旦你持久化到了本地，这个时候，本地的数据是不会删除的! 

# Docker File介绍

 docker file是用来构建dok cer镜像的文件!命令参数脚本! 

构建步骤： 

1、编写一个docker file文件 

2、docker build构建成为一个镜像 

3、docker run运行镜像 

4、docker push发布镜像(Docker Hub、阿里云镜像仓库!) 



Docker Hub搜索镜像centos

![image-20201124123057311](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225904.png)

选择1个版本点击后进入Github

跳转后的路径就是Dockerfile

![image-20201124123219322](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225905.png)

```
FROM scratch
ADD centos-7-x86_64-docker.tar.xz /

LABEL \
    org.label-schema.schema-version="1.0" \
    org.label-schema.name="CentOS Base Image" \
    org.label-schema.vendor="CentOS" \
    org.label-schema.license="GPLv2" \
    org.label-schema.build-date="20200809" \
    org.opencontainers.image.title="CentOS Base Image" \
    org.opencontainers.image.vendor="CentOS" \
    org.opencontainers.image.licenses="GPL-2.0-only" \
    org.opencontainers.image.created="2020-08-09 00:00:00+01:00"

CMD ["/bin/bash"]
```

很多官方镜像都是基础包，很多功能没有，我们通常会自己搭建自己的镜像! 

官方既然可以制作镜像，那我们也可以! 

## Docker File构建过程 

基础知识： 

1、每个保留关键字(指令)都是必须是大写字母

 2、执行从上到下顺序执行 

3、#表示注释 

4、每一个指令都会创建提交一个新的镜像层，并提交! 

![image-20201124123231531](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225906.png)

dockerfile是面向开发的，我们以后要发布项目，做镜像，就需要编写dockerfile文件， 这个文件十分简单! 

Docker镜像逐渐成为企业交付的标准，必须要掌握! 

步骤：

DockerFile：构建文件， 定义了一切的步骤， 源代码 

Dockerlmages：通过Docker File构建生成的镜像， 最终发布和运行的产品!

Docker容器：容器就是镜像运行起来提供服务的

开发，部署，运维。。。缺一不可! 

## Docker File指令

```shell
FROM 						#基础镜镜像，一切从这里开始构建 

MAINTAINER 					#镜像是谁写的，姓名+邮箱 

RUN 						#镜像构建的时候需要运行的命令 

ADD 						#步骤：tomcat镜像， 这个tomcat压缩包!添加内容 

WORKDIR 					#镜像的工作目录 

VOLUME 						#挂载的目录 

EXPOSE 						#暴露端口配置 

CMD							#指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代 

ENTRYPOINT 					#指定这个容器启动的时候要运行的命令，可以追加命令 

ON BUILD 					#当构建一个被继承Docker File这个时候就会运行ON BUILD 的指令。触发指令。 

COPY 						#类似ADD， 将我们文件拷贝到镜像中 ENV #构建的时候设置环境变量! 
```

## 实战测试

Docker Hub中99%镜像都是从这个基础镜像过来的FROM scratch， 然后配置需要的软件和配置来进行的构建。

![image-20201128120846285](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225907.png)

## 构建自己的镜像

默认的centos镜像只包含了最基础的东西

![image-20201124123439691](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225908.png)

## 编写dockerfile配置文件

创建/data目录，再创建dockerfile目录，用来专门存放dockerfile文件。

编写一个dockerfile文件，命名为dockerfile-centos

![image-20201124123505586](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225909.png)

```
FROM centos
MAINTAINER lwenwu<lwenwu1999@qq.com>

ENV MYPATH /usr/local
WORKDIR $MYPATH
 
RUN yum -y install vim
RUN yum -y install net-tools
 
EXPOSE 80
 
CMD echo $MYPATH
CMD echo "-------end--------"
CMD /bin/bash
```

![image-20201124123607319](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225910.png)

## 通过dockerfile文件构建镜像

```
docker build -f /data/dockerfile/dockerfile-centos -t mycentos:0.1 .
```



```shell
[root@localhost dockerfile]# docker build -f /data/dockerfile/dockerfile-centos -t mycentos:0.1 .
Sending build context to Docker daemon  2.048kB		#发送build信息
Step 1/10 : FROM centos
 ---> 0d120b6ccaa8             #拿到基础镜像，跟docker images下的ID相同，复用基础镜像
Step 2/10 : MAINTAINER lwenwu<lwenwu1999@qq.com>		#维护者信息
 ---> Running in 26a8e7585dcd
Removing intermediate container 26a8e7585dcd
 ---> df741b928f75
Step 3/10 : ENV MYPATH /usr/local
 ---> Running in 7b723400348d
Removing intermediate container 7b723400348d
 ---> fc0f488845c1
Step 4/10 : WORKDIR $MYPATH
 ---> Running in 94198e6a23cb
Removing intermediate container 94198e6a23cb
 ---> df3275a301cf
Step 5/10 : RUN yum -y install vim		#下载vim
 ---> Running in 48e8afc0df08
CentOS-8 - AppStream                            605 kB/s | 5.8 MB     00:09    
CentOS-8 - Base                                 2.2 MB/s | 2.2 MB     00:00    
CentOS-8 - Extras                                10 kB/s | 8.1 kB     00:00    
Dependencies resolved.
================================================================================
 Package             Arch        Version                   Repository      Size
================================================================================
Installing:
 vim-enhanced        x86_64      2:8.0.1763-13.el8         AppStream      1.4 M
Installing dependencies:
 gpm-libs            x86_64      1.20.7-15.el8             AppStream       39 k
 vim-common          x86_64      2:8.0.1763-13.el8         AppStream      6.3 M
 vim-filesystem      noarch      2:8.0.1763-13.el8         AppStream       48 k
 which               x86_64      2.21-12.el8               BaseOS          49 k

Transaction Summary
================================================================================
Install  5 Packages

Total download size: 7.8 M
Installed size: 31 M
Downloading Packages:
(1/5): gpm-libs-1.20.7-15.el8.x86_64.rpm         51 kB/s |  39 kB     00:00    
(2/5): vim-filesystem-8.0.1763-13.el8.noarch.rp 314 kB/s |  48 kB     00:00    
(3/5): vim-enhanced-8.0.1763-13.el8.x86_64.rpm  1.3 MB/s | 1.4 MB     00:01    
(4/5): which-2.21-12.el8.x86_64.rpm             314 kB/s |  49 kB     00:00    
(5/5): vim-common-8.0.1763-13.el8.x86_64.rpm    1.8 MB/s | 6.3 MB     00:03    
--------------------------------------------------------------------------------
Total                                           1.7 MB/s | 7.8 MB     00:04  
#下载警告，没什么问题
warning: /var/cache/dnf/AppStream-02e86d1c976ab532/packages/gpm-libs-1.20.7-15.el8.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID 8483c65d: NOKEY
CentOS-8 - AppStream                            158 kB/s | 1.6 kB     00:00    
Importing GPG key 0x8483C65D:
 Userid     : "CentOS (CentOS Official Signing Key) <security@centos.org>"
 Fingerprint: 99DB 70FA E1D7 CE22 7FB6 4882 05B5 55B3 8483 C65D
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : which-2.21-12.el8.x86_64                               1/5 
  Installing       : vim-filesystem-2:8.0.1763-13.el8.noarch                2/5 
  Installing       : vim-common-2:8.0.1763-13.el8.x86_64                    3/5 
  Installing       : gpm-libs-1.20.7-15.el8.x86_64                          4/5 
  Running scriptlet: gpm-libs-1.20.7-15.el8.x86_64                          4/5 
  Installing       : vim-enhanced-2:8.0.1763-13.el8.x86_64                  5/5 
  Running scriptlet: vim-enhanced-2:8.0.1763-13.el8.x86_64                  5/5 
  Running scriptlet: vim-common-2:8.0.1763-13.el8.x86_64                    5/5 
  Verifying        : gpm-libs-1.20.7-15.el8.x86_64                          1/5 
  Verifying        : vim-common-2:8.0.1763-13.el8.x86_64                    2/5 
  Verifying        : vim-enhanced-2:8.0.1763-13.el8.x86_64                  3/5 
  Verifying        : vim-filesystem-2:8.0.1763-13.el8.noarch                4/5 
  Verifying        : which-2.21-12.el8.x86_64                               5/5 

Installed:
  gpm-libs-1.20.7-15.el8.x86_64         vim-common-2:8.0.1763-13.el8.x86_64    
  vim-enhanced-2:8.0.1763-13.el8.x86_64 vim-filesystem-2:8.0.1763-13.el8.noarch
  which-2.21-12.el8.x86_64             

Complete!		#编译成功
Removing intermediate container 48e8afc0df08
 ---> 3e3387c3a894
Step 6/10 : RUN yum -y install net-tools		#下载net-tools
 ---> Running in 90f391b8fe89
Last metadata expiration check: 0:00:12 ago on Thu Nov  5 13:18:48 2020.
Dependencies resolved.
================================================================================
 Package         Architecture Version                        Repository    Size
================================================================================
Installing:
 net-tools       x86_64       2.0-0.51.20160912git.el8       BaseOS       323 k

Transaction Summary
================================================================================
Install  1 Package

Total download size: 323 k
Installed size: 1.0 M
Downloading Packages:
net-tools-2.0-0.51.20160912git.el8.x86_64.rpm   1.4 MB/s | 323 kB     00:00    
--------------------------------------------------------------------------------
Total                                           184 kB/s | 323 kB     00:01     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : net-tools-2.0-0.51.20160912git.el8.x86_64              1/1 
  Running scriptlet: net-tools-2.0-0.51.20160912git.el8.x86_64              1/1 
  Verifying        : net-tools-2.0-0.51.20160912git.el8.x86_64              1/1 

Installed:
  net-tools-2.0-0.51.20160912git.el8.x86_64                                     

Complete!		#又编译成功
Removing intermediate container 90f391b8fe89
 ---> da4ad4cd2938
Step 7/10 : EXPOSE 80
 ---> Running in 96f829f08850
Removing intermediate container 96f829f08850
 ---> 3d2d0365e5c7
Step 8/10 : CMD echo $MYPATH
 ---> Running in 00344184eafe
Removing intermediate container 00344184eafe
 ---> 005ee0708a17
Step 9/10 : CMD echo "-------end--------"
 ---> Running in c7019a9bcfd9
Removing intermediate container c7019a9bcfd9
 ---> c964b172bf9e
Step 10/10 : CMD /bin/bash
 ---> Running in 9900c5470588
Removing intermediate container 9900c5470588
 ---> f804e311e9aa
Successfully built f804e311e9aa
Successfully tagged mycentos:0.1		#构建完成
[root@localhost dockerfile]#
```

## 测试运行

查看构建的镜像

![image-20201124123707158](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225911.png)

运行构建的容器

```shell
docker run -it mycentos:0.1		#使用镜像名称要加版本号,否则会下载最新的镜像
```

构建的镜像vim ifconfig命令可以使用，工作目录为配置的/usr/local

![image-20201124123907532](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225912.png)

## 查看镜像构建历史

```
docker history ID
```

![image-20201124124149432](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225913.png)

## 查看官方镜像是如何构建的

![image-20201124124305978](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225914.png)

通过查看官方镜像的构建历史可以学习镜像是如何构建的。

## CMD和ENTRYPOINT区别

CMD							#指定这个容器启动的时候要运行的命令，只有最后一个会生效，可被替代 

ENTRYPOINT 					#指定这个容器启动的时候要运行的命令，可以追加命令 

### 测试CMD

只有最后一个会执行

进入dockerfile目录，编写dockerfile-cmd-test文件

![image-20201124124339187](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225915.png)

构建镜像

```
docker build -f dockerfile-cmd-test -t cmdtest .

```

![image-20201124124412279](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225916.png)

执行镜像，ls -a命令生效

```
docker run ID
```

![image-20201124124444972](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225917.png)

追加-l命令参数测试,

```shell
docker: Error response from daemon: OCI runtime create failed: container_linux.go:349: starting container process caused "exec: \"-l\": executable file not found in $PATH": unknown.

```

![image-20201124124521479](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225918.png)

追加的-l命令替换了CMD["ls""-a"]命令，-l不是命令，所以报错。

![image-20201124124558731](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225919.png)

命令被替换

### 测试ENTRYPOINT

进入dockerfile目录，编写dockerfile-entrypoint-test文件

![image-20201124124716741](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225920.png)

构建镜像

```
docker build -f dockerfile-entrypoint-test -t entrytest .
```

![image-20201124124751576](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225921.png)

执行镜像，ls -a命令生效

```
docker run ID
```

![image-20201124125037417](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225922.png)

追加-l命令参数测试

```
docker run 4c60442a1328 -l
```

追加-l生效

![image-20201124124851195](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225923.png)

不会替换掉dockerfile文件中的内容。

# 实战Tomcat镜像

## TomCat目录结构说明

```shell
#TomCat目录结构说明：
bin：该目录存放TomCat二进制可执行文件，常用的有startup.bat和shutdown.bat文件，startup.bat用来启动Tomcat，shutdown.bat用来停止Tomcat；
conf：TomCat服务器的配置目录，主要有server.xml（配置服务器信息，如修改端口号，添加虚拟主机等）、tomcat-users.xml（TomCat用户与角色信息，对TomCat后台管理）和web.xml（Web项目部署描述符文件）；
lib：Tomcat所需的jar包；
logs：存放TomCat的日志文件；
temp：存放Tomcat的临时文件；
webapps：存放所部署的Web项目；
work：存放Web项目部署运行时生成的文件，如java和class文件；
RUNNING.txt：可查看如何配置TomCat环境变量。

#TomCat配置环境变量

Tomcat是Java应用程序，不直接使用环境变量。
环境变量由Tomcat启动脚本使用。脚本使用
环境变量来准备启动Tomcat的命令。

（3.1）设置CATALINA_HOME（必填）和CATALINA_BASE（可选）

CATALINA_HOME环境变量应设置为
Tomcat“二进制”分发的根目录。

Tomcat启动脚本具有一些逻辑来设置此变量
如果不存在，则根据启动脚本的位置自动进行
在* nix中和Windows的当前目录中。该逻辑可能不起作用在所有情况下，建议显式设置变量。

CATALINA_BASE环境变量指定根的位置
Tomcat“活动配置”的目录。它是可选的。它默认等于CATALINA_HOME。
```



```shell
#jdk目录结构说明

bin目录：Java工具的可执行文件，包括: java、Java编译器javac、反编译.class文件javap、密钥管理工具keytool、Java文档工具javadoc等。
COPYRIGHT文件：版权信息。
db目录：Java实现的数据库。
include目录：.h头文件，C语言开发时用到的头文件。比如jni.h是开发jni程序时必须引用的头文件。
lib目录： Java类库，我们经常看到的dt.jar和tools.jar就在这个目录下。
src.zip文件：Java类库源码，包括了rt.jar库中的关键部分；除了Java类库，还包含了启动器（launcher）的源码（C语言实现）。
jre目录：Java运行环境。

#jdk配置环境变量

JDK安装完成后，首先要配置JAVA_HOME变量，JAVA_HOME变量指向JDK的安装目录，配置JAVA_HOME主要目的是： 
（1）配置其它JDK环境变量时，可以方便地引用JDK的安装目录。

（2）JDK安装完成后，需要配置Path环境变量，以方便开发者运行Java编译器等程序。开发者不管是用集成开发工具还是文本编辑工具编写Java程序时，当集成开发工具调用Java编译器或用户在Windows 命令行窗口输入命令运行Java编译器时，操作系统需要从Path环境变量获取Java编译器等程序所在目录并启动运行。例如：假设Java集成开发工具或Windows 命令行窗口的当前工作目录和Java编译器所在目录不同，开发者又没有在path环境变量中配置Java编译器所在目录的路径，操作系统就找不到Java编译器程序，也就无法启动Java编译器程序进行编译工作。

（3）Java源代码被被编译后形成扩展名为“.class”的文件，JVM（Java虚拟机）运行Java 程序时，需要加载已被编译的“.class”的文件以及该“.class”文件导入的其它类（如Java的System类）。设置CLASSPATH的目的就是让JVM能够通过CLASSPATH设置的路径找到这些类文件

ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
告诉jvm要使用或执行的class放在什么路径上，便于JVM加载class文件，.;表示当前路径，tools.jar和dt.jar为类库路径。

CLASSPATH详解：
tools.jar
	工具类库(编译和运行等)，它跟我们程序中用到的基础类库没有关系。我们注意到在Path中变量值bin目录下的各个exe工具的大小都很小，一般都在27KB左右，这是因为它们实际上仅仅相当于是一层代码的包装，这些工具的实现所要用到的类库都在tools.jar中，用压缩软件打开tools.jar,你会发现有很多文件是和bin目录下的exe工具相对性的，查看图一。当然，如果tools.jar的功能只有这些的话，那么我们根本不用把它加入到CLASSPATH变量中，因为bin目录下的工具自己可以完成对这些类库的调用，因此tools.jar应该还有其他的功能。在里面还可以看到有Applet和RMI等相关的文件，因此tools.jar应该还是远程调用等必须的jar包。tools.jar的其他作用可以查看其他资料。

dt.jar
	运行环境类库，主要是Swing包，这一点通过用压缩软件打开dt.jar也可以看到。如果在开发时候没有用到Swing包，那么可以不用将dt.jar添加到CLASSPATH变量中。

CLASSPATH中的类库是由Application ClassLoader或者我们自定义的类加载器来加载的，这里当然不能包括基础类库，如果包括基础类库的话，并用两个不同的自定义类加载器去加载该基础类，那它得到的该基础类就不是唯一的了，这样便不能保证Java类的安全性。

基本类库和扩展类库rt.jar
	基本类库是所有的 import java.* 开头的类，在 %JAVA_HOME%\jre\lib 目录下（如其中的 rt.jar、resource.jar ），类加载机制提到，该目录下的类会由 Bootstrap ClassLoader 自动加载，并通过亲委派模型保证了基础类库只会被Bootstrap ClassLoader加载，这也就保证了基础类的唯一性。
	扩展类库是所有的 import javax.* 开头的类，在 %JAVA_HOME%\jre\lib\ext 目录下，该目录下的类是由Extension ClassLoader 自动加载，不需要我们指定。
```



## 准备镜像文件

准备镜像文件、tomcat压缩包、jdk压缩包。

```
apache-tomcat-9.0.39.tar
```

```
jdk-8u271-linux-x64.tar
```

![image-20201125120826748](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225924.png)

## 编写Dockerfile文件

官方命名：Dockerfile，build会自动寻找这个文件，就不需要-f指定了！

```
容器内部/usr/local目录下就会看到readme.txt这个文件
将压缩包添加进去 跟解压路径
注：用ADD命令添加进去的.tar.gz文件会自动解压
安装基础的命令
设置ENV环境变量 进去的时候就进入到环境变量
配置工作目录

配置JAVA环境变量

配置Tomcat环境变量

暴露端口

```

```
FROM centos
MAINTAINER lwenwu<lwenwu1999@qq.com>

COPY readme.txt /usr/local/readme.txt

ADD jdk-8u271-linux-x64.tar.gz /usr/local
ADD apache-tomcat-9.0.39.tar.gz /usr/local

RUN yum -y install vim

ENV MYPATH /usr/local
WORKDIR $MYPATH

ENV JAVA_HOME /usr/local/jdk1.8.0_271
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

ENV CATALINA_HOME /usr/local/apache-tomcat-9.0.39
ENV CATALINA_BASE /usr/local/apache-tomcat-9.0.39
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib:$CATALINA_HOME/bin

EXPOSE 8080

CMD /usr/local/apache-tomcat-9.0.39/bin/startup.sh && tail -F /usr/local/apache-tomcat-9.0.39/logs/catalina.out
```

![image-20201125120906603](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225925.png)

## 构建镜像

```
docker build -t diytomcat .
```

## 构建过程

```
[root@localhost dockerfile]# docker build -t testtomcat .
Sending build context to Docker daemon  154.4MB
Step 1/15 : FROM centos
latest: Pulling from library/centos
3c72a8ed6814: Pull complete 
Digest: sha256:76d24f3ba3317fa945743bb3746fbaf3a0b752f10b10376960de01da70685fbd
Status: Downloaded newer image for centos:latest
 ---> 0d120b6ccaa8
Step 2/15 : MAINTAINER lwenwu<lwenwu1999@qq.com>
 ---> Running in 47b5eb8df66b
Removing intermediate container 47b5eb8df66b
 ---> 49bcdfea4e32
Step 3/15 : COPY readme.txt /usr/local/readme.txt
 ---> 2a6be7198e44
Step 4/15 : ADD jdk-8u271-linux-x64.tar.gz /usr/local
 ---> 88e1646ee66d
Step 5/15 : ADD apache-tomcat-9.0.39.tar.gz /usr/local
 ---> 259ee757cb6f
Step 6/15 : RUN yum -y install vim
 ---> Running in 2d1b5f504afa
CentOS-8 - AppStream                            3.3 MB/s | 5.8 MB     00:01    
CentOS-8 - Base                                 2.5 MB/s | 2.2 MB     00:00    
CentOS-8 - Extras                                13 kB/s | 8.1 kB     00:00    
Dependencies resolved.
================================================================================
 Package             Arch        Version                   Repository      Size
================================================================================
Installing:
 vim-enhanced        x86_64      2:8.0.1763-13.el8         AppStream      1.4 M
Installing dependencies:
 gpm-libs            x86_64      1.20.7-15.el8             AppStream       39 k
 vim-common          x86_64      2:8.0.1763-13.el8         AppStream      6.3 M
 vim-filesystem      noarch      2:8.0.1763-13.el8         AppStream       48 k
 which               x86_64      2.21-12.el8               BaseOS          49 k

Transaction Summary
================================================================================
Install  5 Packages

Total download size: 7.8 M
Installed size: 31 M
Downloading Packages:
(1/5): gpm-libs-1.20.7-15.el8.x86_64.rpm        176 kB/s |  39 kB     00:00    
(2/5): vim-filesystem-8.0.1763-13.el8.noarch.rp 697 kB/s |  48 kB     00:00    
(3/5): which-2.21-12.el8.x86_64.rpm             474 kB/s |  49 kB     00:00    
(4/5): vim-enhanced-8.0.1763-13.el8.x86_64.rpm  1.6 MB/s | 1.4 MB     00:00    
(5/5): vim-common-8.0.1763-13.el8.x86_64.rpm    4.2 MB/s | 6.3 MB     00:01    
--------------------------------------------------------------------------------
Total                                           2.2 MB/s | 7.8 MB     00:03     
warning: /var/cache/dnf/AppStream-02e86d1c976ab532/packages/gpm-libs-1.20.7-15.el8.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID 8483c65d: NOKEY
CentOS-8 - AppStream                            825 kB/s | 1.6 kB     00:00    
Importing GPG key 0x8483C65D:
 Userid     : "CentOS (CentOS Official Signing Key) <security@centos.org>"
 Fingerprint: 99DB 70FA E1D7 CE22 7FB6 4882 05B5 55B3 8483 C65D
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : which-2.21-12.el8.x86_64                               1/5 
  Installing       : vim-filesystem-2:8.0.1763-13.el8.noarch                2/5 
  Installing       : vim-common-2:8.0.1763-13.el8.x86_64                    3/5 
  Installing       : gpm-libs-1.20.7-15.el8.x86_64                          4/5 
  Running scriptlet: gpm-libs-1.20.7-15.el8.x86_64                          4/5 
  Installing       : vim-enhanced-2:8.0.1763-13.el8.x86_64                  5/5 
  Running scriptlet: vim-enhanced-2:8.0.1763-13.el8.x86_64                  5/5 
  Running scriptlet: vim-common-2:8.0.1763-13.el8.x86_64                    5/5 
  Verifying        : gpm-libs-1.20.7-15.el8.x86_64                          1/5 
  Verifying        : vim-common-2:8.0.1763-13.el8.x86_64                    2/5 
  Verifying        : vim-enhanced-2:8.0.1763-13.el8.x86_64                  3/5 
  Verifying        : vim-filesystem-2:8.0.1763-13.el8.noarch                4/5 
  Verifying        : which-2.21-12.el8.x86_64                               5/5 

Installed:
  gpm-libs-1.20.7-15.el8.x86_64         vim-common-2:8.0.1763-13.el8.x86_64    
  vim-enhanced-2:8.0.1763-13.el8.x86_64 vim-filesystem-2:8.0.1763-13.el8.noarch
  which-2.21-12.el8.x86_64             

Complete!
Removing intermediate container 2d1b5f504afa
 ---> 104e56b60aec
Step 7/15 : ENV MYPATH /usr/local
 ---> Running in 9582f9a31cee
Removing intermediate container 9582f9a31cee
 ---> dd0e414f6f83
Step 8/15 : WORKDIR $MYPATH
 ---> Running in 5a1b9e7b62c7
Removing intermediate container 5a1b9e7b62c7
 ---> 4a2e99caa954
Step 9/15 : ENV JAVA_HOME /usr/local/jdk1.8.0_271
 ---> Running in 4d8ee0c67b7b
Removing intermediate container 4d8ee0c67b7b
 ---> 8da62fbac351
Step 10/15 : ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
 ---> Running in 065821bf046e
Removing intermediate container 065821bf046e
 ---> ad73e38ee464
Step 11/15 : ENV CATALINA_HOME /usr/local/apache-tomcat-9.0.39
 ---> Running in 4792108504fd
Removing intermediate container 4792108504fd
 ---> e5ad1371c5c4
Step 12/15 : ENV CATALINA_BASE /usr/local/apache-tomcat-9.0.39
 ---> Running in 62dbef974ce0
Removing intermediate container 62dbef974ce0
 ---> a494ad3353e3
Step 13/15 : ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib:$CATALINA_HOME/bin
 ---> Running in 2cc75de94c1e
Removing intermediate container 2cc75de94c1e
 ---> 06bec94756ec
Step 14/15 : EXPOSE 8080
 ---> Running in ccbe33eefb43
Removing intermediate container ccbe33eefb43
 ---> 75e040b2f7c3
Step 15/15 : CMD /usr/local/apache-tomcat-9.0.39/bin/startup.sh && tail -F /usr/local/apache-tomcat-9.0.39/logs/catalina.out
 ---> Running in ad622bea20ad
Removing intermediate container ad622bea20ad
 ---> 13aa57b24d7f
Successfully built 13aa57b24d7f
Successfully tagged testtomcat:latest

```

## 查看镜像

```
docker images
```

![image-20201125120940544](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225926.png)

## 后台运行容器

-d：后台运行

挂载目录

```
docker run -d -p 9090:8080 --name tomcattest -v /data/tomcat/test:/usr/local/apache-tomcat-9.0.39/webapps/test -v /data/tomcat/logs:/usr/local/apache-tomcat-9.0.39/logs testtomcat
```

![image-20201125121021192](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225927.png)

## 测试挂载

容器内：

![image-20201125121054136](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225928.png)

容器外：

![image-20201125121126026](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225929.png)

## 进入容器

查看运行容器

```
docker ps
```

![image-20201125121153936](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225930.png)

进入容器

```
docker exec -it ID /bin/bash
```

![image-20201125121230183](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225931.png)

## 访问测试

容器外面测试

```
curl localhost:9090
```

```
[root@localhost data]# curl localhost:9090



<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <title>Apache Tomcat/9.0.39</title>
        <link href="favicon.ico" rel="icon" type="image/x-icon" />
        <link href="favicon.ico" rel="shortcut icon" type="image/x-icon" />
        <link href="tomcat.css" rel="stylesheet" type="text/css" />
    </head>

    <body>
        <div id="wrapper">
            <div id="navigation" class="curved container">
                <span id="nav-home"><a href="https://tomcat.apache.org/">Home</a></span>
                <span id="nav-hosts"><a href="/docs/">Documentation</a></span>
                <span id="nav-config"><a href="/docs/config/">Configuration</a></span>
                <span id="nav-examples"><a href="/examples/">Examples</a></span>
                <span id="nav-wiki"><a href="https://wiki.apache.org/tomcat/FrontPage">Wiki</a></span>
                <span id="nav-lists"><a href="https://tomcat.apache.org/lists.html">Mailing Lists</a></span>
                <span id="nav-help"><a href="https://tomcat.apache.org/findhelp.html">Find Help</a></span>
                <br class="separator" />
            </div>
            <div id="asf-box">
                <h1>Apache Tomcat/9.0.39</h1>
            </div>
            <div id="upper" class="curved container">
                <div id="congrats" class="curved container">
                    <h2>If you're seeing this, you've successfully installed Tomcat. Congratulations!</h2>
                </div>
                <div id="notice">
                    <img src="tomcat.png" alt="[tomcat logo]" />
                    <div id="tasks">
                        <h3>Recommended Reading:</h3>
                        <h4><a href="/docs/security-howto.html">Security Considerations How-To</a></h4>
                        <h4><a href="/docs/manager-howto.html">Manager Application How-To</a></h4>
                        <h4><a href="/docs/cluster-howto.html">Clustering/Session Replication How-To</a></h4>
                    </div>
                </div>
                <div id="actions">
                    <div class="button">
                        <a class="container shadow" href="/manager/status"><span>Server Status</span></a>
                    </div>
                    <div class="button">
                        <a class="container shadow" href="/manager/html"><span>Manager App</span></a>
                    </div>
                    <div class="button">
                        <a class="container shadow" href="/host-manager/html"><span>Host Manager</span></a>
                    </div>
                </div>
                <br class="separator" />
            </div>
            <div id="middle" class="curved container">
                <h3>Developer Quick Start</h3>
                <div class="col25">
                    <div class="container">
                        <p><a href="/docs/setup.html">Tomcat Setup</a></p>
                        <p><a href="/docs/appdev/">First Web Application</a></p>
                    </div>
                </div>
                <div class="col25">
                    <div class="container">
                        <p><a href="/docs/realm-howto.html">Realms &amp; AAA</a></p>
                        <p><a href="/docs/jndi-datasource-examples-howto.html">JDBC DataSources</a></p>
                    </div>
                </div>
                <div class="col25">
                    <div class="container">
                        <p><a href="/examples/">Examples</a></p>
                    </div>
                </div>
                <div class="col25">
                    <div class="container">
                        <p><a href="https://wiki.apache.org/tomcat/Specifications">Servlet Specifications</a></p>
                        <p><a href="https://wiki.apache.org/tomcat/TomcatVersions">Tomcat Versions</a></p>
                    </div>
                </div>
                <br class="separator" />
            </div>
            <div id="lower">
                <div id="low-manage" class="">
                    <div class="curved container">
                        <h3>Managing Tomcat</h3>
                        <p>For security, access to the <a href="/manager/html">manager webapp</a> is restricted.
                        Users are defined in:</p>
                        <pre>$CATALINA_HOME/conf/tomcat-users.xml</pre>
                        <p>In Tomcat 9.0 access to the manager application is split between
                           different users. &nbsp; <a href="/docs/manager-howto.html">Read more...</a></p>
                        <br />
                        <h4><a href="/docs/RELEASE-NOTES.txt">Release Notes</a></h4>
                        <h4><a href="/docs/changelog.html">Changelog</a></h4>
                        <h4><a href="https://tomcat.apache.org/migration.html">Migration Guide</a></h4>
                        <h4><a href="https://tomcat.apache.org/security.html">Security Notices</a></h4>
                    </div>
                </div>
                <div id="low-docs" class="">
                    <div class="curved container">
                        <h3>Documentation</h3>
                        <h4><a href="/docs/">Tomcat 9.0 Documentation</a></h4>
                        <h4><a href="/docs/config/">Tomcat 9.0 Configuration</a></h4>
                        <h4><a href="https://wiki.apache.org/tomcat/FrontPage">Tomcat Wiki</a></h4>
                        <p>Find additional important configuration information in:</p>
                        <pre>$CATALINA_HOME/RUNNING.txt</pre>
                        <p>Developers may be interested in:</p>
                        <ul>
                            <li><a href="https://tomcat.apache.org/bugreport.html">Tomcat 9.0 Bug Database</a></li>
                            <li><a href="/docs/api/index.html">Tomcat 9.0 JavaDocs</a></li>
                            <li><a href="https://github.com/apache/tomcat/tree/master">Tomcat 9.0 Git Repository at GitHub</a></li>
                        </ul>
                    </div>
                </div>
                <div id="low-help" class="">
                    <div class="curved container">
                        <h3>Getting Help</h3>
                        <h4><a href="https://tomcat.apache.org/faq/">FAQ</a> and <a href="https://tomcat.apache.org/lists.html">Mailing Lists</a></h4>
                        <p>The following mailing lists are available:</p>
                        <ul>
                            <li id="list-announce"><strong><a href="https://tomcat.apache.org/lists.html#tomcat-announce">tomcat-announce</a><br />
                                Important announcements, releases, security vulnerability notifications. (Low volume).</strong>
                            </li>
                            <li><a href="https://tomcat.apache.org/lists.html#tomcat-users">tomcat-users</a><br />
                                User support and discussion
                            </li>
                            <li><a href="https://tomcat.apache.org/lists.html#taglibs-user">taglibs-user</a><br />
                                User support and discussion for <a href="https://tomcat.apache.org/taglibs/">Apache Taglibs</a>
                            </li>
                            <li><a href="https://tomcat.apache.org/lists.html#tomcat-dev">tomcat-dev</a><br />
                                Development mailing list, including commit messages
                            </li>
                        </ul>
                    </div>
                </div>
                <br class="separator" />
            </div>
            <div id="footer" class="curved container">
                <div class="col20">
                    <div class="container">
                        <h4>Other Downloads</h4>
                        <ul>
                            <li><a href="https://tomcat.apache.org/download-connectors.cgi">Tomcat Connectors</a></li>
                            <li><a href="https://tomcat.apache.org/download-native.cgi">Tomcat Native</a></li>
                            <li><a href="https://tomcat.apache.org/taglibs/">Taglibs</a></li>
                            <li><a href="/docs/deployer-howto.html">Deployer</a></li>
                        </ul>
                    </div>
                </div>
                <div class="col20">
                    <div class="container">
                        <h4>Other Documentation</h4>
                        <ul>
                            <li><a href="https://tomcat.apache.org/connectors-doc/">Tomcat Connectors</a></li>
                            <li><a href="https://tomcat.apache.org/connectors-doc/">mod_jk Documentation</a></li>
                            <li><a href="https://tomcat.apache.org/native-doc/">Tomcat Native</a></li>
                            <li><a href="/docs/deployer-howto.html">Deployer</a></li>
                        </ul>
                    </div>
                </div>
                <div class="col20">
                    <div class="container">
                        <h4>Get Involved</h4>
                        <ul>
                            <li><a href="https://tomcat.apache.org/getinvolved.html">Overview</a></li>
                            <li><a href="https://tomcat.apache.org/source.html">Source Repositories</a></li>
                            <li><a href="https://tomcat.apache.org/lists.html">Mailing Lists</a></li>
                            <li><a href="https://wiki.apache.org/tomcat/FrontPage">Wiki</a></li>
                        </ul>
                    </div>
                </div>
                <div class="col20">
                    <div class="container">
                        <h4>Miscellaneous</h4>
                        <ul>
                            <li><a href="https://tomcat.apache.org/contact.html">Contact</a></li>
                            <li><a href="https://tomcat.apache.org/legal.html">Legal</a></li>
                            <li><a href="https://www.apache.org/foundation/sponsorship.html">Sponsorship</a></li>
                            <li><a href="https://www.apache.org/foundation/thanks.html">Thanks</a></li>
                        </ul>
                    </div>
                </div>
                <div class="col20">
                    <div class="container">
                        <h4>Apache Software Foundation</h4>
                        <ul>
                            <li><a href="https://tomcat.apache.org/whoweare.html">Who We Are</a></li>
                            <li><a href="https://tomcat.apache.org/heritage.html">Heritage</a></li>
                            <li><a href="https://www.apache.org">Apache Home</a></li>
                            <li><a href="https://tomcat.apache.org/resources.html">Resources</a></li>
                        </ul>
                    </div>
                </div>
                <br class="separator" />
            </div>
            <p class="copyright">Copyright &copy;1999-2020 Apache Software Foundation.  All Rights Reserved</p>
        </div>
    </body>

</html>
[root@localhost data]#
```

网页测试

```
http://192.168.100.100:9090
```

![image-20201125121312587](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225932.png)

【坑】报错日志：

```
/usr/local/apache-tomcat-9.0.39/bin/catalina.sh: line 502: /usr/local/jdk.1.8.0.27/bin/java: No such file or directory
/usr/local/apache-tomcat-9.0.39/bin/catalina.sh: line 502: /usr/local/jdk.1.8.0.27/bin/java: No such file or directory
```

分析修改环境变量

```shell
#ENV JAVA_HOME /usr/local/jdk1.8.0_271		java环境变量错误，导致后面引用的变量都错误，最终导致Tomcat没有启动成功。
```

## html测试

web.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
                             http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
         version="2.5">

</web-app>
```

index.jsp

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>hello.lwenwu！</title>
</head>
<body>
Hello World!<br/>
<%
out.println("this is a test file");
%>
</body>
</html>
```

失败

![image-20201125121400983](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225933.png)

分析：

# 发布镜像

## 发布镜像到DockerHub

1.地址:https://hub.docker.com/，注册账号。

2.dockler login帮助命令

-u		#用户

-p		#密码

```
Usage:	docker login [OPTIONS] [SERVER]

Log in to a Docker registry.
If no server is specified, the default is defined by the daemon.

Options:
  -p, --password string   Password
      --password-stdin    Take the password from stdin
  -u, --username string   Username
```

![image-20201125121725703](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225934.png)

3.登录账号

```
[root@localhost ~]# docker login -u lwenwu
Password: 
```

![image-20201125121801207](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225935.png)

4.服务器登陆后提交自己的镜像，docker push 

push时需要带上作者的名字，镜像需要带上版本号，否则会拒绝，本地镜像的TAG标签要改成	账号/名称:tag	才能push成功。

错误：

![image-20201125121833349](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225936.png)

增加TAG,给当前镜像增加TAG标签。

注：本地镜像的TAG标签要改成	账号/名称:tag	才能push成功。

```
docker tag 13aa57b24d7f lwenwu/tomcat:1.0
```

修改后会多出一个

![image-20201125121900586](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225937.png)

再次提交

```
docker push lwenwu/tomcat:1.0
```

```
[root@localhost ~]# docker push lwenwu/tomcat:1.0
The push refers to repository [docker.io/lwenwu/tomcat]
fbf49d42cce1: Pushed 
ab05fe66e378: Pushed 
947e7a54038d: Pushed 
9fb962ef813e: Pushed 
291f6e44771a: Mounted from library/centos 
1.0: digest: sha256:9ee0258534ff11bcfefc26fd1f2f5ca2e048f07736ecb7102e5be97c9190c673 size: 1373
```

提交也是按照镜像的层级进行提交的！

![image-20201125121929718](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225938.png)

## 发布镜像到阿里云

1.登录阿里云

https://cr.console.aliyun.com/cn-hangzhou/instances/repositories

2.找到容器镜像服务

3.创建命名空间

命令空间：项目

![image-20201125122002506](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225939.png)

一个账号最多可以创建 3 个命名空间命名空间。

![image-20201125122447547](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225940.png)

![image-20201125122524629](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225941.png)

4.创建镜像仓库

![image-20201125122554331](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225942.png)

![image-20201125122628043](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225943.png)

![image-20201125122652503](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225944.png)

5.仓库信息

![image-20201125122740121](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225945.png)



```
1. 登录阿里云Docker Registry
$ sudo docker login --username=lwenwu1999 registry.cn-hangzhou.aliyuncs.com
用于登录的用户名为阿里云账号全名，密码为开通服务时设置的密码。

您可以在访问凭证页面修改凭证密码。

2. 从Registry中拉取镜像
$ sudo docker pull registry.cn-hangzhou.aliyuncs.com/lwenwu/docker:[镜像版本号]
3. 将镜像推送到Registry
$ sudo docker login --username=lwenwu1999 registry.cn-hangzhou.aliyuncs.com
$ sudo docker tag [ImageId] registry.cn-hangzhou.aliyuncs.com/lwenwu/docker:[镜像版本号]
$ sudo docker push registry.cn-hangzhou.aliyuncs.com/lwenwu/docker:[镜像版本号]
请根据实际镜像信息替换示例中的[ImageId]和[镜像版本号]参数。

4. 选择合适的镜像仓库地址
从ECS推送镜像时，可以选择使用镜像仓库内网地址。推送速度将得到提升并且将不会损耗您的公网流量。

如果您使用的机器位于VPC网络，请使用 registry-vpc.cn-hangzhou.aliyuncs.com 作为Registry的域名登录。
```

6.登录阿里云Docker Registry

```
docker login --username=lwenwu1999 registry.cn-hangzhou.aliyuncs.com
```

![image-20201125122825062](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225946.png)

7.将镜像推送到Registry

错误

![image-20201125122904517](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225947.png)

解决：

严格按照官方说明进行TAG标签修改，然后push。

![image-20201125122940072](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225948.png)

```
docker push registry.cn-hangzhou.aliyuncs.com/lwenwu/tomcat:1.0
```

![image-20201128120704967](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225949.png)

## docker流程总结



![image-20201125123226157](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225950.png)

![image-20201125123247144](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225951.png)

# Docker网络

## 理解docker0

首先清空所有镜像，保证干净环境。

```
docker rmi -f $(docker images -a -q)
```

lo:	#本机回环地址

eth0:	#本机网卡地址

docker0:docker0地址

![image-20201125181516348](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225952.png)

docker是如何处理容器网络访问的？

测试

```
docker run -d -P --name tomcat01 tomcat
```

![image-20201125181547337](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225953.png)

查看容器内部的网络地址

```
docker exec -it tomcat01 ip addr
```

```
[root@localhost ~]# docker exec -it tomcat01 ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
4: eth0@if5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever
[root@localhost ~]#
```

发现容器启动的时候会得到一个docker分配的eth0@if5 网卡。

![image-20201125181642151](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225954.png)

linux宿主机能不能ping通容器内的IP地址？

测试

结果：linux主机可以ping通容器内部

![image-20201125181711416](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225955.png)

容器内是否可以ping通linux主机?

测试

结果：容器内否可以ping通linux主机。

![image-20201125181749042](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225956.png)

docker0相当于家庭中的路由器，负责给网段内的主机分配IP地址。

## docker0原理

1.我们每启动一个docker容器， docker就会给docker容器分配一个ip， 我们只要安装了docker， 就会有一个网卡docker 0 ,采用桥接模式， 使用的技术是ev th-pair技术!

![image-20201125181827412](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225957.png)

2.启动容器再次测试ipaddr，发现多了一个网卡。

结论：启动一个容器linux宿主机会多出1个对应的网卡。

![image-20201128120636298](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225958.png)

3.容器内和容器外网卡是相互绑定的。

容器内：

![image-20201125181928295](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112225959.png)

容器外：

![image-20201125181956931](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230000.png)

4.再启动一个容器进行测试。

![image-20201125182023416](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230001.png)

结论：启动N个容器linux宿主机会多出N个对应的网卡。

```shell
#我们发现这个容器带来网卡，都是相互绑定的。 
#veth-pair就是一对的虚拟设备接口， 他们都是相互绑定出现的， 一段连着协议， 一段彼此相连 
#正因为有这个特性， veth-pair充当一个桥梁， 连接各种虚拟网络设备的 
#OpenStak，Docker容器之间的连接，ovS的连接，都是使用veth-pair技术. 
```

## 容器间通信

测试容器之间是否可以互相通信？

tomcat01

![image-20201125182113385](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230002.png)

tomcat02

![image-20201125182137267](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230003.png)

测试ping

![image-20201125182215137](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230004.png)

![image-20201125182238152](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230005.png)

都能互相ping通。

知识：

可以不进入容器来ping。

```
docker exec -it tomcat02 ping 172.17.0.2
```

![image-20201125182423639](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230006.png)

结论：容器和容器间是可以互相ping通的！

Docker0网络模型图：

![image-20201125182456761](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230007.png)

结论：Docker使用的是Linux的桥接， 宿主机中是一个Dokcer容器的网桥docker0。 

![image-20201125182515030](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230008.png)

虚拟网卡，Docker中的所有的网络接口都是虚拟的。虚拟的转发效率高! (内网传递文件!) 

## 移除容器查看网卡

移除容器后网卡自动消失

测试

![image-20201126124404253](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230009.png)

注：只要删除容器，对应的网卡就会删除！

## --link

场景：容器IP变更，不影响通信，以docker容器名称进行ping通信。

启动容器tomcat01和tomcat02

![image-20201126124435543](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230010.png)

测试：用容器名称ping测试通信。

```
docker exec -it tomcat01 ping tomcat02
```

![image-20201126124505333](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230011.png)

## 解决容器名称互通

如何可以解决？

再启动一个容器tomcat03,增加--link参数，测试通信。

```
docker run -d -P --name tomcat03 --link tomcat02 tomcat
```

![image-20201126124603957](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230012.png)

测试用容器名称ping

```
docker exec -it tomcat03 ping tomcat02
```

![image-20201126124637596](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230013.png)

## 反向ping测试

[坑]反向ping测试

![image-20201126124712500](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230014.png)

## docker network究竟

```
[root@localhost ~]# docker network --help

Usage:	docker network COMMAND

Manage networks

Commands:
  connect     Connect a container to a network
  create      Create a network
  disconnect  Disconnect a container from a network
  inspect     Display detailed information on one or more networks
  ls          List networks
  prune       Remove all unused networks
  rm          Remove one or more networks
```

![image-20201126124743448](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230015.png)

查看docker0 bridge网卡详细信息

docker0网卡

```
docker network inspect 991190b12345
```

![image-20201126124810504](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230016.png)

容器分配的地址信息

![image-20201126124847112](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230017.png)

查看容器tomcat03的详细信息

![image-20201126124922581](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230018.png)

```
docker inspect fc39850d8b31
```

![image-20201126124949594](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230019.png)

拓展：

```
docker inspect conID|grep tomcat03 -n
```

![image-20201126125051369](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230020.png)

查看tomcat03容器的hosts文件

```
docker exec -it fc39850d8b31 cat /etc/hosts
```

![image-20201126125131973](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230021.png)

本质探究：--link就是我们在hosts配置文件中增加了1个tomcat02的映射。

不建议使用--link,因为--link需要相互绑定才能互相通信。

docker0问题：不支持容器名互相连接访问！

# 容器互联

docker0问题：不支持容器名互相连接访问！

查看所有的docker网络

```sh
docker network ls
```

![image-20201127120406425](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230022.png)

## 网络模式

bridge：桥接docker默认，自定义的网络也使用bridge模式。

none：不配置网络。

host：和宿主机共享网络。

container：容器内网络连通！用的少！局限很大！

## docker network帮助信息

```
[root@localhost ~]# docker network --help

Usage:	docker network COMMAND

Manage networks

Commands:
  connect     Connect a container to a network
  create      Create a network
  disconnect  Disconnect a container from a network
  inspect     Display detailed information on one or more networks
  ls          List networks
  prune       Remove all unused networks
  rm          Remove one or more networks
```

![image-20201127120439881](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230023.png)

## 测试自定义网络

删除所有容器，保证干净环境。

```
docker rm -f $(docker ps -a -q)
```

![image-20201127120508537](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230024.png)

回到最初的3个网卡

![image-20201127120539887](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230025.png)

之前直接启动的的命令

```shell
docker run -d -P --name tomcat01 tomcat
#直接启动的容器默认是docker0网络，其实默认省略了--net bridge参数
```

docker0特点，默认域名不能访问，--link需要互相打通才能相互通信，不建议使用。

## 自定义网络

![image-20201127120610090](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230026.png)

再查看docker network create --help帮助信息

```
docker network create --help
```

![image-20201127120732970](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230027.png)

创建一个自定义网络

--driver bridge					#默认为桥接，可不写

--subnet 192.168.0.0/16	#子网

--gateway 192.168.0.1		#路由

```
docker network create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 nettest
```

![image-20201127120805865](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230028.png)

查看创建的网络

```
docker network ls
```

![image-20201127120838263](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230029.png)

查看创建网络的详细信息

```
docker network inspect nettest
```

![image-20201127120913438](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230030.png)

到此自己的网络就创建好了。

## 容器走自定义网络

测试启动2个容器

```
docker run -d -P --name tomcat-net-01 --net nettest tomcat
```

```
docker run -d -P --name tomcat-net-02 --net nettest tomcat
```

![image-20201127120958716](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230031.png)

再次查看自定义网络的详细信息

```
docker network inspect nettest
```

![image-20201127121038238](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230032.png)

此时自定义网络下面就有了我们的容器信息。

## 测试域名ping

```
docker exec -it tomcat-net-01 ping 192.168.0.3
```

```
docker exec -it tomcat-net-01 ping tomcat-net-02
```

![image-20201127121122381](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230033.png)

![image-20201127121151959](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230034.png)

此时用容器的名称可以互相Ping通了。

自定义的网络修复了docker0的缺陷。

## 网络间通信

网络联通，使2张网下的容器也可以互相通信。

启动2个容器，不指定网络。测试2个网络下是否可以互通。

```shell
docker run -d -P --name tomcat01 tomcat
docker run -d -P --name tomcat02 tomcat

#测试
docker exec -it tomcat01 ping tomcat-net-01
```

![image-20201127121236102](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230035.png)

如何打通docker0和自定义的网络？

网络之间如何互相打通？

连接1个容器到1个网络

```
docker network --help
```

![image-20201127121308073](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230036.png)

查看帮助信息

```
docker network connect --help
```

![image-20201127121346380](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230037.png)

测试打通,查看详细信息

```
docker network connect nettest tomcat01
```

![image-20201127121415748](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230038.png)

查看详细信息，连通后发生了什么？

```
docker network inspect nettest
```

![image-20201127121451408](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230039.png)

连通之后就将tomcat01放到了nettest网络下？

测试通信

![image-20201127121527501](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230040.png)

官方：1个容器2个IP

方法：容器和网络打通解决2张网络下容器通信。

测试tomcat02

tomcat02与自定义网络nettest没有打通，所以无法ping通。

![image-20201127121547165](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230041.png)

结论：假设要跨网络通信，就需要使用docker network connect打通！

# 部署Redis集群

分片+高可用+负载均衡

其中一个挂了，备用的顶上

![image-20201127123736321](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230042.png)

redis集群

启动6个容器

## 创建redis集群网卡

```
docker network create redis --subnet 172.38.0.0/16
```

![image-20201127123836346](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230043.png)

查看redis网卡的详细信息

```
docker network inspect redis
```

![image-20201127123909048](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230044.png)

## 配置redis集群

通过脚本创建6个redis配置

```shell
for port in $(seq 1 6); \
do \
mkdir -p /data/redis/node-${port}/conf
touch /data/redis/node-${port}/conf/redis.conf
cat << EOF >/data/redis/node-${port}/conf/redis.conf
port 6379
bind 0.0.0.0
cluster-enabled yes
cluster-config-file nodes.conf
cluster-node-timeout 5000
cluster-announce-ip 172.38.0.1${port}
cluster-announce-port 6379
cluster-announce-bus-port 16379
appendonly yes
EOF
done
```

查看创建的文件

![image-20201127123942205](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230045.png)

## 启动容器

```shell
#脚本
docker run -p 637${port}:6379 -p 1637${port}:16379 --name redis-${port} \
-v /data/redis/node-${port}/data:/data \
-v /data/redis/node-${port}/conf/redis.conf:/etc/redis/redis.conf \
-d --net redis --ip 172.38.0.1${port} redis:5.0.10-alpine3.12 redis-server /etc/redis/redis.conf; \


#手动
docker run -p 6371:6379 -p 16371:16379 --name redis-1 -v /data/redis/node-1/data:/data -v /data/redis/node-1/conf/redis.conf:/etc/redis/redis.conf -d --net redis --ip 172.38.0.11 redis:5.0.10-alpine3.12 redis-server /etc/redis/redis.conf

```

## 查看启动容器

```
docker ps
```

![image-20201127124024008](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230046.png)

## 进入redis容器

redis中没有bash命令，redis进入使用/bin/sh

![image-20201127124056825](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230047.png)

```
docker exec -it IDNAME /bin/sh
```

![image-20201127124229644](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230048.png)

进入后默认的目录为/data

## 创建集群

```
redis-cli --cluster create 172.38.0.11:6379 172.38.0.12:6379 172.38.0.13:6379 172.38.0.14:6379 172.38.0.15:6379 172.38.0.16:6379 --cluster-replicas 1
```

![image-20201127124259322](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230049.png)

集群创建完毕

![image-20201127124406280](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230050.png)

```
#过程
>>> Performing hash slots allocation on 6 nodes...
Master[0] -> Slots 0 - 5460
Master[1] -> Slots 5461 - 10922
Master[2] -> Slots 10923 - 16383
Adding replica 172.38.0.15:6379 to 172.38.0.11:6379
Adding replica 172.38.0.16:6379 to 172.38.0.12:6379
Adding replica 172.38.0.14:6379 to 172.38.0.13:6379
M: 290353fdbf5a7345e66fee97be33fa4e352eadfb 172.38.0.11:6379
   slots:[0-5460] (5461 slots) master
M: 2d341c0a2aac0cd99a4cec112292bc7c48e608e2 172.38.0.12:6379
   slots:[5461-10922] (5462 slots) master
M: 4d1882d9fa8f86d794bfad393ae982be4350338c 172.38.0.13:6379
   slots:[10923-16383] (5461 slots) master
S: 8319c1e759a38114d5208ab329dc241b35289d28 172.38.0.14:6379
   replicates 4d1882d9fa8f86d794bfad393ae982be4350338c
S: 8b81002b5dcef5041c5ca70605c8cc30a53d05e0 172.38.0.15:6379
   replicates 290353fdbf5a7345e66fee97be33fa4e352eadfb
S: 530887eef54e59efe34b2a98f131fdc5cc6e1937 172.38.0.16:6379
   replicates 2d341c0a2aac0cd99a4cec112292bc7c48e608e2
Can I set the above configuration? (type 'yes' to accept): yes
>>> Nodes configuration updated
>>> Assign a different config epoch to each node
>>> Sending CLUSTER MEET messages to join the cluster
Waiting for the cluster to join
.
>>> Performing Cluster Check (using node 172.38.0.11:6379)
M: 290353fdbf5a7345e66fee97be33fa4e352eadfb 172.38.0.11:6379
   slots:[0-5460] (5461 slots) master
   1 additional replica(s)
M: 2d341c0a2aac0cd99a4cec112292bc7c48e608e2 172.38.0.12:6379
   slots:[5461-10922] (5462 slots) master
   1 additional replica(s)
M: 4d1882d9fa8f86d794bfad393ae982be4350338c 172.38.0.13:6379
   slots:[10923-16383] (5461 slots) master
   1 additional replica(s)
S: 8319c1e759a38114d5208ab329dc241b35289d28 172.38.0.14:6379
   slots: (0 slots) slave
   replicates 4d1882d9fa8f86d794bfad393ae982be4350338c
S: 8b81002b5dcef5041c5ca70605c8cc30a53d05e0 172.38.0.15:6379
   slots: (0 slots) slave
   replicates 290353fdbf5a7345e66fee97be33fa4e352eadfb
S: 530887eef54e59efe34b2a98f131fdc5cc6e1937 172.38.0.16:6379
   slots: (0 slots) slave
   replicates 2d341c0a2aac0cd99a4cec112292bc7c48e608e2
[OK] All nodes agree about slots configuration.
>>> Check for open slots...
>>> Check slots coverage...
[OK] All 16384 slots covered.

```

## 连接集群

```
redis-cli -c
```

查看集群信息

```
6379>cluster info
```



![image-20201127124459308](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230051.png)

查看节点信息

```
127.0.0.1:6379>cluster nodes
```

![image-20201127124540041](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230052.png)

注：3主3从

```
set a b
```

主节点在处理

![image-20201127124618858](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230053.png)

从机应该也有一个这样的值，主节点挂了，从节点应该替代上来。（高可用）

## 查看运行的容器

```
docker ps
```

![image-20201127124658184](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230054.png)

## 停掉主节点

```
docker stop ID
```

![image-20201127124725737](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230055.png)

再次get值，连接超时

![image-20201127124751099](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230056.png)

再次连接，get a

![image-20201127124819804](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230057.png)

master失败，从172.38.0.14从节点自动升为主节点

![image-20201127124847082](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230058.png)

Docker搭建redis集群完成！

使用docker之后，所有的技术慢慢变的简单起来！

# SpringBoot微服务打包Docker镜像



## 构建springboot项目



## 打包应用



## 编写dockerfile



## 构建镜像



## 发布运行

## 结语

# docker进阶

## 环境准备

停止docker

```
systemctl stop docker
```

卸载docker引擎

```
yum remove docker-ce docker-ce-cli containerd.io
```

移除docker目录

```
rm -rf /var/lib/docker/
```

> /var/lib/docker/的内容，包括镜像、容器、卷和网络。Docker引擎包现在称为Docker -ce

测试

```
[root@localhost ~]# docker ps
-bash: /usr/bin/docker: No such file or directory
[root@localhost ~]#
```

> 注：已经没有相关命令了

卸载旧版本

```shell
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

> 如果yum报告没有安装这些包，也是可以的。

```
[root@localhost ~]# yum remove docker \
>                   docker-client \
>                   docker-client-latest \
>                   docker-common \
>                   docker-latest \
>                   docker-latest-logrotate \
>                   docker-logrotate \
>                   docker-engine
Loaded plugins: fastestmirror
No Match for argument: docker
No Match for argument: docker-client
No Match for argument: docker-client-latest
No Match for argument: docker-common
No Match for argument: docker-latest
No Match for argument: docker-latest-logrotate
No Match for argument: docker-logrotate
No Match for argument: docker-engine
No Packages marked for removal
[root@localhost ~]# 
```

安装基础包

```shell
yum install -y yum-utils
```

> 安装 yum-utils 包(它提供 yum-config-manager 实用工具)并设置稳定存储库。
>

> 添加镜像仓库
>
> 默认国外源：
> yum-config-manager \
>     --add-repo \
>     https://download.docker.com/linux/centos/docker-ce.repo
>     
> 阿里云：    
> yum-config-manager \
>     --add-repo \
>     http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

更新yum软件包索引

```shell
yum makecache fast
```

安装 Docker引擎

```shell
yum install docker-ce docker-ce-cli containerd.io
```

> 安装特定版本的Docker：
>
> yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io

启动Docker

```
systemctl start docker
systemctl enable docker
```

测试

```
docker version
docker run hello-world
docker images
```

配置镜像加速器

```shell
sudo mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://gnxq79wc.mirror.aliyuncs.com"]
}
EOF

sudo systemctl daemon-reload

sudo systemctl restart docker
```

# Docker Compose

## Docker Compose介绍

https://docs.docker.com/compose/

定义多个容器一键启动所有容器。

YAML 配置文件

命令有哪些？

> 官方介绍

Compose是一个用于定义和运行多容器Docker应用程序的工具。使用Compose，您可以使用一个YAML文件来配置应用程序的服务。然后，使用一个命令，您可以从您的配置中创建并启动所有的服务。要了解有关Compose的所有特性的更多信息，请参阅特性列表。
在所有环境中组合工作:生产、分段、开发、测试，以及CI工作流。您可以在常见用例中了解关于每个用例的更多信息。
使用Compose基本上有三个步骤:

1、用Dockerfile定义应用程序的环境，这样它就可以在任何地方复制。
2、在docker-compose.yml中定义您的应用程序的服务，以便它们可以在隔离的环境中一起运行。
3、运行docker-compose up和Compose starts并运行整个应用程序。

作用：批量容器编排。

自己理解：

Comepose是Docker官方的开源项目，需要安装！

Dockerfile让程序在任何地方运行。web服务、redis、nginx...多个容器。



docker-compose.yml例子：

```
version: "3.9"
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
      - logvolume01:/var/log
    links:
      - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
```

docker compose up 一次启动多个服务。

## Docker Compose概念

Comepose:重要概念

- 服务services，应用（web、redis、mysql）

- 项目project,一组关联的容器。

  

## Compose安装

1、下载

```
官方地址：下载较慢

sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

国内镜像地址：

curl -L https://get.daocloud.io/docker/compose/releases/download/1.27.4/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
```

2、增加可执行权限

```
sudo chmod +x /usr/local/bin/docker-compose
```

确认

```
[root@localhost ~]# docker-compose --version
docker-compose version 1.27.4, build 40524192
[root@localhost ~]#
```

## 开始compose

https://docs.docker.com/compose/gettingstarted/

> 官方说明
>
> 在这个页面上，您构建了一个运行在 Docker Compose 上的简单 Python web 应用程序。该应用程序使用了 Flask 框架，并在 Redis 维护了一个点击计数器。虽然示例使用 Python，但这里演示的概念应该是可以理解的，即使您不熟悉它。先决条件确保您已经安装了 Docker 引擎和 Docker Compose。您不需要安装 Python 或 Redis，因为它们都是由 Docker 映像提供的。

1、定义应用程序的依赖项。为项目创建一个目录

```shell
[root@localhost ~]# cd /data/
[root@localhost data]# mkdir composetest
[root@localhost data]# cd composetest
[root@localhost composetest]#
```

2、在项目目录中创建一个名为app.py的文件,并将以下内容粘贴到文件中

```shell
import time

import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)

def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)

@app.route('/')
def hello():
    count = get_hit_count()
    return 'Hello World! I have been seen {} times.\n'.format(count)
```

> 在此示例中，redis是应用程序网络上的redis容器的主机名。我们为Redis使用默认端口6379。
>
> 注意get_hit_count函数的编写方式。如果redis服务不可用，这个基本的重试循环允许我们多次尝试请求。当应用程序上线时，这在启动时很有用，但是如果在应用程序的生命周期内需要重新启动Redis服务，这也使我们的应用程序更有弹性。在集群中，这也有助于处理节点之间的瞬时连接中断。

3、在项目目录中创建另一个名为requirements.txt的文件，并将以下内容粘贴到文件中

```
[root@localhost composetest]# cat requirements.txt 
flask
redis
[root@localhost composetest]#
```

## 创建Dockerfile

在这一步中，您将编写一个Dockerfile来构建Docker映像。图像包含Python应用程序需要的所有依赖项，包括Python本身。
在项目目录中，创建一个名为Dockerfile的文件并粘贴以下内容：

```
FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
EXPOSE 5000
COPY . .
CMD ["flask", "run"]
```

> 这告诉Docker：
> 从python3.7映像开始构建一个映像。
> 将工作目录设置为/code。
> 设置flask命令使用的环境变量。
> 安装gcc和其他依赖项
> 复制要求.txt并安装Python依赖项。
> 向映像添加元数据，以说明容器正在侦听端口5000
> 复制当前目录。在工程中。在图像中。
> 将容器的默认命令设置为flask run。

## 定义服务

1、在项目目录中创建一个名为docker-compose.yml的文件，然后粘贴以下内容：

```
version: "3.9"
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: "redis:alpine"
```

该Compose文件定义了两个服务：Web和Redis。

Web服务
web服务使用从当前目录中的Dockerfile构建的映像。然后它将容器和主机绑定到公开的端口5000。此示例服务使用Flask web服务器的默认端口5000。
Redis服务
redis服务使用从Docker Hub注册表中提取的公共redis映像。

当前文件夹下的4个文件：

```
[root@localhost composetest]# ll
total 16
-rw-r--r-- 1 root root 514 Dec 14 23:22 app.py
-rw-r--r-- 1 root root 111 Dec 14 23:51 docker-compose.yml
-rw-r--r-- 1 root root 252 Dec 14 23:25 Dockerfile
-rw-r--r-- 1 root root  12 Dec 14 23:21 requirements.txt
[root@localhost composetest]# 
```

## 构建和运行应用

使用Compose构建和运行应用程序。

1、在项目目录中，通过运行docker-compose up来启动应用程序。

```
docker-compose up
```



1.应用app.py

2.Dockerfile 应用打包为镜像

3.Docker-compose.yaml文件（定义整个服务需要的环境、web、redis,完整的上线服务）

4.启动compose项目（docker-compose up）

## 告警解决

流程：

创建网络—执行Docker-compose.yaml文件—启动服务。

中途报警提示镜像不存在，执行docker-compose build

```
[root@localhost composetest]# docker-compose build
redis uses an image, skipping
Building web
Step 1/10 : FROM python:3.7-alpine
 ---> 0ce5215b0b31
Step 2/10 : WORKDIR /code
 ---> Using cache
 ---> ba1f9f199b82
Step 3/10 : ENV FLASK_APP=app.py
 ---> Using cache
 ---> 2fc74b01a73d
Step 4/10 : ENV FLASK_RUN_HOST=0.0.0.0
 ---> Using cache
 ---> 32b4aa9e96e0
Step 5/10 : RUN apk add --no-cache gcc musl-dev linux-headers
 ---> Using cache
 ---> 950b055b2a97
Step 6/10 : COPY requirements.txt requirements.txt
 ---> Using cache
 ---> 7bf0bce3d7a9
Step 7/10 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> e18eb5e5bafb
Step 8/10 : EXPOSE 5000
 ---> Using cache
 ---> a66622c4cc0f
Step 9/10 : COPY . .
 ---> Using cache
 ---> 42114f1ec656
Step 10/10 : CMD ["flask", "run"]
 ---> Using cache
 ---> 0f443e7f92e4

Successfully built 0f443e7f92e4
Successfully tagged composetest_web:latest
[root@localhost composetest]# 
```

再次执行docker-compose up，启动成功

```
[root@localhost composetest]# docker-compose up
Starting composetest_redis_1 ... done
Starting composetest_web_1   ... done
Attaching to composetest_redis_1, composetest_web_1
redis_1  | 1:C 16 Dec 2020 04:22:40.307 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis_1  | 1:C 16 Dec 2020 04:22:40.307 # Redis version=6.0.9, bits=64, commit=00000000, modified=0, pid=1, just started
redis_1  | 1:C 16 Dec 2020 04:22:40.307 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis_1  | 1:M 16 Dec 2020 04:22:40.307 * Running mode=standalone, port=6379.
redis_1  | 1:M 16 Dec 2020 04:22:40.307 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
redis_1  | 1:M 16 Dec 2020 04:22:40.307 # Server initialized
redis_1  | 1:M 16 Dec 2020 04:22:40.307 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
redis_1  | 1:M 16 Dec 2020 04:22:40.307 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo madvise > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled (set to 'madvise' or 'never').
redis_1  | 1:M 16 Dec 2020 04:22:40.320 * Loading RDB produced by version 6.0.9
redis_1  | 1:M 16 Dec 2020 04:22:40.320 * RDB age 79370 seconds
redis_1  | 1:M 16 Dec 2020 04:22:40.320 * RDB memory usage when created 0.77 Mb
redis_1  | 1:M 16 Dec 2020 04:22:40.320 * DB loaded from disk: 0.012 seconds
redis_1  | 1:M 16 Dec 2020 04:22:40.320 * Ready to accept connections
web_1    |  * Serving Flask app "app.py"
web_1    |  * Environment: production
web_1    |    WARNING: This is a development server. Do not use it in a production deployment.
web_1    |    Use a production WSGI server instead.
web_1    |  * Debug mode: off
web_1    |  * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
```

![image-20201216122756684](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230059.png)

访问5000端口,计数器：每访问一次加一。

```
[root@localhost ~]# curl localhost:5000
Hello World! I have been seen 1 times.
[root@localhost ~]# curl localhost:5000
Hello World! I have been seen 2 times.
[root@localhost ~]# curl localhost:5000
Hello World! I have been seen 3 times.
[root@localhost ~]# curl localhost:5000
Hello World! I have been seen 4 times.
[root@localhost ~]# curl localhost:5000
Hello World! I have been seen 5 times.
[root@localhost ~]#
```

对应前面文件app.py中的内容

```
import time

import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)

def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)

@app.route('/')
def hello():
    count = get_hit_count()
    return 'Hello World! I have been seen {} times.\n'.format(count)
```

查看运行的容器,服务启动成功。

````
[root@localhost ~]# docker ps
CONTAINER ID   IMAGE             COMMAND                  CREATED        STATUS              PORTS                    NAMES
4fbea3b1e5c1   composetest_web   "flask run"              23 hours ago   Up About a minute   0.0.0.0:5000->5000/tcp   composetest_web_1
061c25816933   redis:alpine      "docker-entrypoint.s…"   23 hours ago   Up About a minute   6379/tcp                 composetest_redis_1
[root@localhost ~]# 
````

查看镜像

```
[root@localhost ~]# docker images
REPOSITORY        TAG          IMAGE ID       CREATED         SIZE
composetest_web   latest       0f443e7f92e4   47 hours ago    196MB
redis             alpine       f731cd48185c   5 days ago      31.6MB
python            3.7-alpine   0ce5215b0b31   5 days ago      41.1MB
hello-world       latest       bf756fb1ae65   11 months ago   13.3kB
[root@localhost ~]# 
```

以前都需要run下载镜像，现在通过docker-compose.yml会自动构建。

composetest_web

redis

python

## 服务规则

composetest_web_1

composetest_redis_1

文件名____________服务名___________num数字

生产环境：

多个服务器搭建集群。

集群环境：

服务redis—多个副本，服务不可能只有一个运行实例，真实环境都是弹性、负载均衡、高可用。

## 查看所有服务

因为不是集群，所以该命令无法查看服务。需要swarm集群。

```
[root@localhost ~]# docker service ls
Error response from daemon: This node is not a swarm manager. Use "docker swarm init" or "docker swarm join" to connect this node to swarm and try again.
[root@localhost ~]#
```

## 网络规则

```
[root@localhost ~]# docker network ls
NETWORK ID     NAME                  DRIVER    SCOPE
bea25d6732f1   bridge                bridge    local
d2a12aac3c49   composetest_default   bridge    local
0638c33a175f   host                  host      local
943386457d17   none                  null      local
[root@localhost ~]#
```

composetest_default:

通过compose启动就会生产一个自己的网络。

10个服务=>项目

项目中的内容都在同一个网络下，域名访问。

## 查看网络信息

```
[root@localhost ~]# docker  network inspect composetest_default
[
    {
        "Name": "composetest_default",
        "Id": "d2a12aac3c494f30b43bfbf1cac3668eb2fdfab004fba1de973ea053328e813b",
        "Created": "2020-12-14T23:58:05.062718888-05:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": true,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "061c2581693361daca9dd9b1c8e613658e22233c5a327a3a8b01ceff78c276db": {
                "Name": "composetest_redis_1",
                "EndpointID": "da79080b268347d234943fa0c8e021010e32decde0a56a46a7eba4b61b2ae04c",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            },
            "4fbea3b1e5c1f2eb880d73422f6af97121c47c13f706cef2dfc384aa8d66a26e": {
                "Name": "composetest_web_1",
                "EndpointID": "1b980f3b031dc64c76bd9b1fd7aeb9232fd1339f477813750e13866c4173c634",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {
            "com.docker.compose.network": "default",
            "com.docker.compose.project": "composetest",
            "com.docker.compose.version": "1.27.4"
        }
    }
]
[root@localhost ~]#
```

"Containers":

web和redis都在同一个网络下，可以直接通过域名访问。

```
cache = redis.Redis(host='redis', port=6379)
```

> 前面文件中没有写实际的IP，而是host='redis',这样做的好处就是假如一个服务挂了，再次拉起一个服务，此时IP会变更，而采用host这种方式服务即使挂掉再拉起一个同样可以直接通过域名来访问。

## 停止服务

必须在当前文件目录下

```
docker-compose down
```

或在如下页面

按Ctrl+C

![image-20201217130253879](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230100.png)

以前都是单个docker run启动容器。

现在可以通过

docker-compose编写yaml配置文件编写服务，再通过docker-compose up一键启动或停止所有服务。

## YAML编写规则

https://docs.docker.com/compose/compose-file/

核心：3层。

官网例子：

https://docs.docker.com/compose/compose-file/compose-file-v3/

```

version: "3.9"
services:

  redis:
    image: redis:alpine
    ports:
      - "6379"
    networks:
      - frontend
    deploy:
      replicas: 2
      update_config:
        parallelism: 2
        delay: 10s
      restart_policy:
        condition: on-failure

  db:
    image: postgres:9.4
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - backend
    deploy:
      placement:
        max_replicas_per_node: 1
        constraints:
          - "node.role==manager"

  vote:
    image: dockersamples/examplevotingapp_vote:before
    ports:
      - "5000:80"
    networks:
      - frontend
    depends_on:
      - redis
    deploy:
      replicas: 2
      update_config:
        parallelism: 2
      restart_policy:
        condition: on-failure

  result:
    image: dockersamples/examplevotingapp_result:before
    ports:
      - "5001:80"
    networks:
      - backend
    depends_on:
      - db
    deploy:
      replicas: 1
      update_config:
        parallelism: 2
        delay: 10s
      restart_policy:
        condition: on-failure

  worker:
    image: dockersamples/examplevotingapp_worker
    networks:
      - frontend
      - backend
    deploy:
      mode: replicated
      replicas: 1
      labels: [APP=VOTING]
      restart_policy:
        condition: on-failure
        delay: 10s
        max_attempts: 3
        window: 120s
      placement:
        constraints:
          - "node.role==manager"

  visualizer:
    image: dockersamples/visualizer:stable
    ports:
      - "8080:8080"
    stop_grace_period: 1m30s
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    deploy:
      placement:
        constraints:
          - "node.role==manager"

networks:
  frontend:
  backend:

volumes:
  db-data:
```

第一层：version: "3.9"

第二层：services:以及服务的配置

服务配置参考：https://docs.docker.com/compose/compose-file/compose-file-v3/右边。

- Service configuration reference
  - build
    - [context](https://docs.docker.com/compose/compose-file/compose-file-v3/#context)
    - [dockerfile](https://docs.docker.com/compose/compose-file/compose-file-v3/#dockerfile)
    - [args](https://docs.docker.com/compose/compose-file/compose-file-v3/#args)
    - [cache_from](https://docs.docker.com/compose/compose-file/compose-file-v3/#cache_from)
    - [labels](https://docs.docker.com/compose/compose-file/compose-file-v3/#labels)
    - [network](https://docs.docker.com/compose/compose-file/compose-file-v3/#network)
    - [shm_size](https://docs.docker.com/compose/compose-file/compose-file-v3/#shm_size)
    - [target](https://docs.docker.com/compose/compose-file/compose-file-v3/#target)
  - [cap_add, cap_drop](https://docs.docker.com/compose/compose-file/compose-file-v3/#cap_add-cap_drop)
  - [cgroup_parent](https://docs.docker.com/compose/compose-file/compose-file-v3/#cgroup_parent)
  - [command](https://docs.docker.com/compose/compose-file/compose-file-v3/#command)
  - configs
    - [Short syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#short-syntax)
    - [Long syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#long-syntax)
  - [container_name](https://docs.docker.com/compose/compose-file/compose-file-v3/#container_name)
  - credential_spec
    - [Example gMSA configuration](https://docs.docker.com/compose/compose-file/compose-file-v3/#example-gmsa-configuration)
  - [depends_on](https://docs.docker.com/compose/compose-file/compose-file-v3/#depends_on)
  - deploy
    - [endpoint_mode](https://docs.docker.com/compose/compose-file/compose-file-v3/#endpoint_mode)
    - [labels](https://docs.docker.com/compose/compose-file/compose-file-v3/#labels-1)
    - [mode](https://docs.docker.com/compose/compose-file/compose-file-v3/#mode)
    - [placement](https://docs.docker.com/compose/compose-file/compose-file-v3/#placement)
    - [max_replicas_per_node](https://docs.docker.com/compose/compose-file/compose-file-v3/#max_replicas_per_node)
    - [replicas](https://docs.docker.com/compose/compose-file/compose-file-v3/#replicas)
    - [resources](https://docs.docker.com/compose/compose-file/compose-file-v3/#resources)
    - [restart_policy](https://docs.docker.com/compose/compose-file/compose-file-v3/#restart_policy)
    - [rollback_config](https://docs.docker.com/compose/compose-file/compose-file-v3/#rollback_config)
    - [update_config](https://docs.docker.com/compose/compose-file/compose-file-v3/#update_config)
    - [Not supported for docker stack deploy](https://docs.docker.com/compose/compose-file/compose-file-v3/#not-supported-for-docker-stack-deploy)
  - [devices](https://docs.docker.com/compose/compose-file/compose-file-v3/#devices)
  - [dns](https://docs.docker.com/compose/compose-file/compose-file-v3/#dns)
  - [dns_search](https://docs.docker.com/compose/compose-file/compose-file-v3/#dns_search)
  - [entrypoint](https://docs.docker.com/compose/compose-file/compose-file-v3/#entrypoint)
  - [env_file](https://docs.docker.com/compose/compose-file/compose-file-v3/#env_file)
  - [environment](https://docs.docker.com/compose/compose-file/compose-file-v3/#environment)
  - [expose](https://docs.docker.com/compose/compose-file/compose-file-v3/#expose)
  - [external_links](https://docs.docker.com/compose/compose-file/compose-file-v3/#external_links)
  - [extra_hosts](https://docs.docker.com/compose/compose-file/compose-file-v3/#extra_hosts)
  - [healthcheck](https://docs.docker.com/compose/compose-file/compose-file-v3/#healthcheck)
  - [image](https://docs.docker.com/compose/compose-file/compose-file-v3/#image)
  - [init](https://docs.docker.com/compose/compose-file/compose-file-v3/#init)
  - [isolation](https://docs.docker.com/compose/compose-file/compose-file-v3/#isolation)
  - [labels](https://docs.docker.com/compose/compose-file/compose-file-v3/#labels-2)
  - [links](https://docs.docker.com/compose/compose-file/compose-file-v3/#links)
  - [logging](https://docs.docker.com/compose/compose-file/compose-file-v3/#logging)
  - [network_mode](https://docs.docker.com/compose/compose-file/compose-file-v3/#network_mode)
  - networks
    - [aliases](https://docs.docker.com/compose/compose-file/compose-file-v3/#aliases)
    - [ipv4_address, ipv6_address](https://docs.docker.com/compose/compose-file/compose-file-v3/#ipv4_address-ipv6_address)
  - [pid](https://docs.docker.com/compose/compose-file/compose-file-v3/#pid)
  - ports
    - [Short syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#short-syntax-1)
    - [Long syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#long-syntax-1)
  - [restart](https://docs.docker.com/compose/compose-file/compose-file-v3/#restart)
  - secrets
    - [Short syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#short-syntax-2)
    - [Long syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#long-syntax-2)
  - [security_opt](https://docs.docker.com/compose/compose-file/compose-file-v3/#security_opt)
  - [stop_grace_period](https://docs.docker.com/compose/compose-file/compose-file-v3/#stop_grace_period)
  - [stop_signal](https://docs.docker.com/compose/compose-file/compose-file-v3/#stop_signal)
  - [sysctls](https://docs.docker.com/compose/compose-file/compose-file-v3/#sysctls)
  - [tmpfs](https://docs.docker.com/compose/compose-file/compose-file-v3/#tmpfs)
  - [ulimits](https://docs.docker.com/compose/compose-file/compose-file-v3/#ulimits)
  - [userns_mode](https://docs.docker.com/compose/compose-file/compose-file-v3/#userns_mode)
  - volumes
    - [Short syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#short-syntax-3)
    - [Long syntax](https://docs.docker.com/compose/compose-file/compose-file-v3/#long-syntax-3)
    - [Volumes for services, swarms, and stack files](https://docs.docker.com/compose/compose-file/compose-file-v3/#volumes-for-services-swarms-and-stack-files)
  - [domainname, hostname, ipc, mac_address, privileged, read_only, shm_size, stdin_open, tty, user, working_dir](https://docs.docker.com/compose/compose-file/compose-file-v3/#domainname-hostname-ipc-mac_address-privileged-read_only-shm_size-stdin_open-tty-user-working_dir)
- [Specifying durations](https://docs.docker.com/compose/compose-file/compose-file-v3/#specifying-durations)
- [Specifying byte values](https://docs.docker.com/compose/compose-file/compose-file-v3/#specifying-byte-values)
- Volume configuration reference
  - [driver](https://docs.docker.com/compose/compose-file/compose-file-v3/#driver)
  - [driver_opts](https://docs.docker.com/compose/compose-file/compose-file-v3/#driver_opts)
  - [external](https://docs.docker.com/compose/compose-file/compose-file-v3/#external)
  - [labels](https://docs.docker.com/compose/compose-file/compose-file-v3/#labels-3)
  - [name](https://docs.docker.com/compose/compose-file/compose-file-v3/#name)
- Network configuration reference
  - driver
    - [bridge](https://docs.docker.com/compose/compose-file/compose-file-v3/#bridge)
    - [overlay](https://docs.docker.com/compose/compose-file/compose-file-v3/#overlay)
    - [host or none](https://docs.docker.com/compose/compose-file/compose-file-v3/#host-or-none)
  - [driver_opts](https://docs.docker.com/compose/compose-file/compose-file-v3/#driver_opts-1)
  - [attachable](https://docs.docker.com/compose/compose-file/compose-file-v3/#attachable)
  - [enable_ipv6](https://docs.docker.com/compose/compose-file/compose-file-v3/#enable_ipv6)
  - [ipam](https://docs.docker.com/compose/compose-file/compose-file-v3/#ipam)
  - [internal](https://docs.docker.com/compose/compose-file/compose-file-v3/#internal)
  - [labels](https://docs.docker.com/compose/compose-file/compose-file-v3/#labels-4)
  - [external](https://docs.docker.com/compose/compose-file/compose-file-v3/#external-1)
  - [name](https://docs.docker.com/compose/compose-file/compose-file-v3/#name-1)

第三层：其他配置（volumes、networks、configs）



- [depends_on](https://docs.docker.com/compose/compose-file/compose-file-v3/#depends_on)依赖，确保服务依赖关系正确。

web服务中写depends on,web服务依赖redis和db,所以会优先启动其他2个服务。

- [deploy](https://docs.docker.com/compose/compose-file/compose-file-v3/#deploy)中有个replicas: 6是副本的意思。

## 搭建开源博客

传统：下载程序，安装数据库，配置...

compose编写应用，一键启动！

官网例子：https://docs.docker.com/compose/wordpress/

WordPress是使用[PHP](https://baike.baidu.com/item/PHP/9337)语言开发的博客平台，用户可以在支持PHP和MySQL数据库的[服务器](https://baike.baidu.com/item/服务器/100571)上架设属于自己的网站。也可以把 WordPress当作一个[内容管理系统](https://baike.baidu.com/item/内容管理系统/2683135)（CMS）来使用。

1.创建一个空的项目目录。

```
[root@localhost ~]# cd /data/
[root@localhost data]# mkdir wordpress
[root@localhost data]# ls
composetest  wordpress
[root@localhost data]#
```

2.切换到项目目录。

```
[root@localhost data]# cd wordpress/
[root@localhost wordpress]# ls
[root@localhost wordpress]# 
```

3.创建一个 docker-compose。一个 yml 文件，用于启动你的 WordPress 博客和一个独立的 MySQL 实例，它有一个数据持久性的卷装载.

> 提示: 您可以为这个文件使用.yml 或.yaml 扩展名，都可以工作。

```
[root@localhost wordpress]# vim docker-compose.yml
```

```
version: '3.3'

services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
```

> 备注：
>
> depends_on：依赖于上一个
>
> environment:环境配置
>
> 启动一个wordpress依赖于mysql。

4.从项目目录运行 docker-compose up -d

> docker-compose up -d:后台启动

启动过程：

```
[root@localhost wordpress]# docker-compose up -d
Creating network "wordpress_default" with the default driver
Creating volume "wordpress_db_data" with default driver
Pulling db (mysql:5.7)...
5.7: Pulling from library/mysql
6ec7b7d162b2: Pull complete
fedd960d3481: Pull complete
7ab947313861: Pull complete
64f92f19e638: Pull complete
3e80b17bff96: Pull complete
014e976799f9: Pull complete
59ae84fee1b3: Pull complete
7d1da2a18e2e: Pull complete
301a28b700b9: Pull complete
529dc8dbeaf3: Pull complete
bc9d021dc13f: Pull complete
Digest: sha256:c3a567d3e3ad8b05dfce401ed08f0f6bf3f3b64cc17694979d5f2e5d78e10173
Status: Downloaded newer image for mysql:5.7
Pulling wordpress (wordpress:latest)...
latest: Pulling from library/wordpress
6ec7b7d162b2: Already exists
db606474d60c: Pull complete
afb30f0cd8e0: Pull complete
3bb2e8051594: Pull complete
4c761b44e2cc: Pull complete
c2199db96575: Pull complete
1b9a9381eea8: Pull complete
50450ffc67ee: Pull complete
4d1e5a768e83: Pull complete
5e8be0d1df16: Pull complete
7a6395859d40: Pull complete
7306499d3dce: Pull complete
fa6f0ba15ac6: Pull complete
308a9ead128f: Pull complete
2db781a8732e: Pull complete
63d3161e9e46: Pull complete
a08dd591ed8a: Pull complete
931a26282f2a: Pull complete
f5c6b405e809: Pull complete
caf2bb847f73: Pull complete
Digest: sha256:dadd8e9c2ef6dc2fe146cbc5f2edc0ed8ae1026ae252b52f25791be4d7d16600
Status: Downloaded newer image for wordpress:latest
Creating wordpress_db_1 ... done
Creating wordpress_wordpress_1 ... done
[root@localhost wordpress]# docker-compose up -d
wordpress_db_1 is up-to-date
wordpress_wordpress_1 is up-to-date
[root@localhost wordpress]# docker-compose up
wordpress_db_1 is up-to-date
wordpress_wordpress_1 is up-to-date
Attaching to wordpress_db_1, wordpress_wordpress_1
db_1         | 2021-01-06 09:19:34+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 5.7.32-1debian10 started.
db_1         | 2021-01-06 09:19:34+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'
db_1         | 2021-01-06 09:19:34+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 5.7.32-1debian10 started.
db_1         | 2021-01-06 09:19:34+00:00 [Note] [Entrypoint]: Initializing database files
db_1         | 2021-01-06T09:19:35.000436Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
db_1         | 2021-01-06T09:19:35.482173Z 0 [Warning] InnoDB: New log files created, LSN=45790
db_1         | 2021-01-06T09:19:35.597659Z 0 [Warning] InnoDB: Creating foreign key constraint system tables.
db_1         | 2021-01-06T09:19:35.678204Z 0 [Warning] No existing UUID has been found, so we assume that this is the first time that this server has been started. Generating a new UUID: 4b32e97d-5000-11eb-8c6b-0242ac130002.
db_1         | 2021-01-06T09:19:35.682249Z 0 [Warning] Gtid table is not ready to be used. Table 'mysql.gtid_executed' cannot be opened.
db_1         | 2021-01-06T09:19:36.436871Z 0 [Warning] CA certificate ca.pem is self signed.
db_1         | 2021-01-06T09:19:36.664740Z 1 [Warning] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
db_1         | 2021-01-06 09:19:38+00:00 [Note] [Entrypoint]: Database files initialized
db_1         | 2021-01-06 09:19:38+00:00 [Note] [Entrypoint]: Starting temporary server
db_1         | 2021-01-06 09:19:38+00:00 [Note] [Entrypoint]: Waiting for server startup
db_1         | 2021-01-06T09:19:39.125099Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
db_1         | 2021-01-06T09:19:39.133047Z 0 [Note] mysqld (mysqld 5.7.32) starting as process 77 ...
db_1         | 2021-01-06T09:19:39.176985Z 0 [Note] InnoDB: PUNCH HOLE support available
db_1         | 2021-01-06T09:19:39.177009Z 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
db_1         | 2021-01-06T09:19:39.177012Z 0 [Note] InnoDB: Uses event mutexes
db_1         | 2021-01-06T09:19:39.177014Z 0 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
db_1         | 2021-01-06T09:19:39.177016Z 0 [Note] InnoDB: Compressed tables use zlib 1.2.11
db_1         | 2021-01-06T09:19:39.177019Z 0 [Note] InnoDB: Using Linux native AIO
db_1         | 2021-01-06T09:19:39.177210Z 0 [Note] InnoDB: Number of pools: 1
db_1         | 2021-01-06T09:19:39.177390Z 0 [Note] InnoDB: Using CPU crc32 instructions
db_1         | 2021-01-06T09:19:39.181520Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
db_1         | 2021-01-06T09:19:39.194255Z 0 [Note] InnoDB: Completed initialization of buffer pool
db_1         | 2021-01-06T09:19:39.202793Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
db_1         | 2021-01-06T09:19:39.222672Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
db_1         | 2021-01-06T09:19:39.260853Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
db_1         | 2021-01-06T09:19:39.260954Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
db_1         | 2021-01-06T09:19:39.312019Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
db_1         | 2021-01-06T09:19:39.321067Z 0 [Note] InnoDB: 96 redo rollback segment(s) found. 96 redo rollback segment(s) are active.
db_1         | 2021-01-06T09:19:39.321123Z 0 [Note] InnoDB: 32 non-redo rollback segment(s) are active.
db_1         | 2021-01-06T09:19:39.325037Z 0 [Note] InnoDB: Waiting for purge to start
db_1         | 2021-01-06T09:19:39.376297Z 0 [Note] InnoDB: 5.7.32 started; log sequence number 2746702
db_1         | 2021-01-06T09:19:39.378041Z 0 [Note] Plugin 'FEDERATED' is disabled.
db_1         | 2021-01-06T09:19:39.387166Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
db_1         | 2021-01-06T09:19:39.417925Z 0 [Note] InnoDB: Buffer pool(s) load completed at 210106  9:19:39
db_1         | 2021-01-06T09:19:39.426605Z 0 [Note] Found ca.pem, server-cert.pem and server-key.pem in data directory. Trying to enable SSL support using them.
db_1         | 2021-01-06T09:19:39.426627Z 0 [Note] Skipping generation of SSL certificates as certificate files are present in data directory.
db_1         | 2021-01-06T09:19:39.427642Z 0 [Warning] CA certificate ca.pem is self signed.
db_1         | 2021-01-06T09:19:39.427726Z 0 [Note] Skipping generation of RSA key pair as key files are present in data directory.
db_1         | 2021-01-06T09:19:39.431945Z 0 [Warning] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
db_1         | 2021-01-06T09:19:39.443443Z 0 [Note] Event Scheduler: Loaded 0 events
db_1         | 2021-01-06T09:19:39.443720Z 0 [Note] mysqld: ready for connections.
db_1         | Version: '5.7.32'  socket: '/var/run/mysqld/mysqld.sock'  port: 0  MySQL Community Server (GPL)
db_1         | 2021-01-06 09:19:39+00:00 [Note] [Entrypoint]: Temporary server started.
db_1         | Warning: Unable to load '/usr/share/zoneinfo/iso3166.tab' as time zone. Skipping it.
db_1         | Warning: Unable to load '/usr/share/zoneinfo/leap-seconds.list' as time zone. Skipping it.
db_1         | Warning: Unable to load '/usr/share/zoneinfo/zone.tab' as time zone. Skipping it.
db_1         | Warning: Unable to load '/usr/share/zoneinfo/zone1970.tab' as time zone. Skipping it.
db_1         | 2021-01-06 09:19:41+00:00 [Note] [Entrypoint]: Creating database wordpress
db_1         | 2021-01-06 09:19:41+00:00 [Note] [Entrypoint]: Creating user wordpress
db_1         | 2021-01-06 09:19:41+00:00 [Note] [Entrypoint]: Giving user wordpress access to schema wordpress
db_1         | 
db_1         | 2021-01-06 09:19:41+00:00 [Note] [Entrypoint]: Stopping temporary server
db_1         | 2021-01-06T09:19:41.455747Z 0 [Note] Giving 0 client threads a chance to die gracefully
db_1         | 2021-01-06T09:19:41.455763Z 0 [Note] Shutting down slave threads
db_1         | 2021-01-06T09:19:41.455769Z 0 [Note] Forcefully disconnecting 0 remaining clients
db_1         | 2021-01-06T09:19:41.455773Z 0 [Note] Event Scheduler: Purging the queue. 0 events
db_1         | 2021-01-06T09:19:41.455919Z 0 [Note] Binlog end
db_1         | 2021-01-06T09:19:41.456361Z 0 [Note] Shutting down plugin 'ngram'
db_1         | 2021-01-06T09:19:41.456368Z 0 [Note] Shutting down plugin 'partition'
db_1         | 2021-01-06T09:19:41.456370Z 0 [Note] Shutting down plugin 'BLACKHOLE'
db_1         | 2021-01-06T09:19:41.456372Z 0 [Note] Shutting down plugin 'ARCHIVE'
db_1         | 2021-01-06T09:19:41.456374Z 0 [Note] Shutting down plugin 'PERFORMANCE_SCHEMA'
db_1         | 2021-01-06T09:19:41.456391Z 0 [Note] Shutting down plugin 'MRG_MYISAM'
db_1         | 2021-01-06T09:19:41.456395Z 0 [Note] Shutting down plugin 'MyISAM'
db_1         | 2021-01-06T09:19:41.456400Z 0 [Note] Shutting down plugin 'INNODB_SYS_VIRTUAL'
db_1         | 2021-01-06T09:19:41.456402Z 0 [Note] Shutting down plugin 'INNODB_SYS_DATAFILES'
db_1         | 2021-01-06T09:19:41.456404Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESPACES'
db_1         | 2021-01-06T09:19:41.456405Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN_COLS'
db_1         | 2021-01-06T09:19:41.456407Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN'
db_1         | 2021-01-06T09:19:41.456408Z 0 [Note] Shutting down plugin 'INNODB_SYS_FIELDS'
db_1         | 2021-01-06T09:19:41.456410Z 0 [Note] Shutting down plugin 'INNODB_SYS_COLUMNS'
db_1         | 2021-01-06T09:19:41.456411Z 0 [Note] Shutting down plugin 'INNODB_SYS_INDEXES'
db_1         | 2021-01-06T09:19:41.456413Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESTATS'
db_1         | 2021-01-06T09:19:41.456414Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLES'
db_1         | 2021-01-06T09:19:41.456416Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_TABLE'
db_1         | 2021-01-06T09:19:41.456417Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_CACHE'
db_1         | 2021-01-06T09:19:41.456419Z 0 [Note] Shutting down plugin 'INNODB_FT_CONFIG'
db_1         | 2021-01-06T09:19:41.456420Z 0 [Note] Shutting down plugin 'INNODB_FT_BEING_DELETED'
db_1         | 2021-01-06T09:19:41.456421Z 0 [Note] Shutting down plugin 'INNODB_FT_DELETED'
db_1         | 2021-01-06T09:19:41.456423Z 0 [Note] Shutting down plugin 'INNODB_FT_DEFAULT_STOPWORD'
db_1         | 2021-01-06T09:19:41.456424Z 0 [Note] Shutting down plugin 'INNODB_METRICS'
db_1         | 2021-01-06T09:19:41.456425Z 0 [Note] Shutting down plugin 'INNODB_TEMP_TABLE_INFO'
db_1         | 2021-01-06T09:19:41.456427Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_POOL_STATS'
db_1         | 2021-01-06T09:19:41.456429Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE_LRU'
db_1         | 2021-01-06T09:19:41.456430Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE'
db_1         | 2021-01-06T09:19:41.456431Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX_RESET'
db_1         | 2021-01-06T09:19:41.456433Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX'
db_1         | 2021-01-06T09:19:41.456434Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM_RESET'
db_1         | 2021-01-06T09:19:41.456435Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM'
db_1         | 2021-01-06T09:19:41.456437Z 0 [Note] Shutting down plugin 'INNODB_CMP_RESET'
db_1         | 2021-01-06T09:19:41.456438Z 0 [Note] Shutting down plugin 'INNODB_CMP'
db_1         | 2021-01-06T09:19:41.456439Z 0 [Note] Shutting down plugin 'INNODB_LOCK_WAITS'
db_1         | 2021-01-06T09:19:41.456441Z 0 [Note] Shutting down plugin 'INNODB_LOCKS'
db_1         | 2021-01-06T09:19:41.456442Z 0 [Note] Shutting down plugin 'INNODB_TRX'
db_1         | 2021-01-06T09:19:41.456444Z 0 [Note] Shutting down plugin 'InnoDB'
db_1         | 2021-01-06T09:19:41.456478Z 0 [Note] InnoDB: FTS optimize thread exiting.
db_1         | 2021-01-06T09:19:41.456713Z 0 [Note] InnoDB: Starting shutdown...
db_1         | 2021-01-06T09:19:41.558263Z 0 [Note] InnoDB: Dumping buffer pool(s) to /var/lib/mysql/ib_buffer_pool
db_1         | 2021-01-06T09:19:41.560067Z 0 [Note] InnoDB: Buffer pool(s) dump completed at 210106  9:19:41
db_1         | 2021-01-06T09:19:43.273861Z 0 [Note] InnoDB: Shutdown completed; log sequence number 12617575
db_1         | 2021-01-06T09:19:43.275009Z 0 [Note] InnoDB: Removed temporary tablespace data file: "ibtmp1"
db_1         | 2021-01-06T09:19:43.275028Z 0 [Note] Shutting down plugin 'MEMORY'
db_1         | 2021-01-06T09:19:43.275037Z 0 [Note] Shutting down plugin 'CSV'
db_1         | 2021-01-06T09:19:43.275041Z 0 [Note] Shutting down plugin 'sha256_password'
db_1         | 2021-01-06T09:19:43.275043Z 0 [Note] Shutting down plugin 'mysql_native_password'
db_1         | 2021-01-06T09:19:43.275124Z 0 [Note] Shutting down plugin 'binlog'
db_1         | 2021-01-06T09:19:43.275626Z 0 [Note] mysqld: Shutdown complete
db_1         | 
db_1         | 2021-01-06 09:19:43+00:00 [Note] [Entrypoint]: Temporary server stopped
db_1         | 
db_1         | 2021-01-06 09:19:43+00:00 [Note] [Entrypoint]: MySQL init process done. Ready for start up.
db_1         | 
db_1         | 2021-01-06T09:19:43.638878Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
db_1         | 2021-01-06T09:19:43.640547Z 0 [Note] mysqld (mysqld 5.7.32) starting as process 1 ...
db_1         | 2021-01-06T09:19:43.644140Z 0 [Note] InnoDB: PUNCH HOLE support available
db_1         | 2021-01-06T09:19:43.644167Z 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
db_1         | 2021-01-06T09:19:43.644171Z 0 [Note] InnoDB: Uses event mutexes
db_1         | 2021-01-06T09:19:43.644237Z 0 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
db_1         | 2021-01-06T09:19:43.644241Z 0 [Note] InnoDB: Compressed tables use zlib 1.2.11
db_1         | 2021-01-06T09:19:43.644246Z 0 [Note] InnoDB: Using Linux native AIO
db_1         | 2021-01-06T09:19:43.644413Z 0 [Note] InnoDB: Number of pools: 1
db_1         | 2021-01-06T09:19:43.644521Z 0 [Note] InnoDB: Using CPU crc32 instructions
db_1         | 2021-01-06T09:19:43.645817Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
db_1         | 2021-01-06T09:19:43.652932Z 0 [Note] InnoDB: Completed initialization of buffer pool
db_1         | 2021-01-06T09:19:43.654891Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
db_1         | 2021-01-06T09:19:43.666791Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
db_1         | 2021-01-06T09:19:43.680623Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
db_1         | 2021-01-06T09:19:43.680704Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
db_1         | 2021-01-06T09:19:43.698427Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
db_1         | 2021-01-06T09:19:43.698911Z 0 [Note] InnoDB: 96 redo rollback segment(s) found. 96 redo rollback segment(s) are active.
db_1         | 2021-01-06T09:19:43.698918Z 0 [Note] InnoDB: 32 non-redo rollback segment(s) are active.
db_1         | 2021-01-06T09:19:43.699150Z 0 [Note] InnoDB: Waiting for purge to start
db_1         | 2021-01-06T09:19:43.750903Z 0 [Note] InnoDB: 5.7.32 started; log sequence number 12617575
db_1         | 2021-01-06T09:19:43.752692Z 0 [Note] Plugin 'FEDERATED' is disabled.
db_1         | 2021-01-06T09:19:43.763484Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
db_1         | 2021-01-06T09:19:43.777047Z 0 [Note] InnoDB: Buffer pool(s) load completed at 210106  9:19:43
db_1         | 2021-01-06T09:19:43.778348Z 0 [Note] Found ca.pem, server-cert.pem and server-key.pem in data directory. Trying to enable SSL support using them.
db_1         | 2021-01-06T09:19:43.778372Z 0 [Note] Skipping generation of SSL certificates as certificate files are present in data directory.
db_1         | 2021-01-06T09:19:43.779331Z 0 [Warning] CA certificate ca.pem is self signed.
db_1         | 2021-01-06T09:19:43.779426Z 0 [Note] Skipping generation of RSA key pair as key files are present in data directory.
db_1         | 2021-01-06T09:19:43.781025Z 0 [Note] Server hostname (bind-address): '*'; port: 3306
db_1         | 2021-01-06T09:19:43.781193Z 0 [Note] IPv6 is available.
db_1         | 2021-01-06T09:19:43.781211Z 0 [Note]   - '::' resolves to '::';
db_1         | 2021-01-06T09:19:43.781254Z 0 [Note] Server socket created on IP: '::'.
db_1         | 2021-01-06T09:19:43.783683Z 0 [Warning] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
db_1         | 2021-01-06T09:19:43.792136Z 0 [Note] Event Scheduler: Loaded 0 events
db_1         | 2021-01-06T09:19:43.792261Z 0 [Note] mysqld: ready for connections.
db_1         | Version: '5.7.32'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
wordpress_1  | WordPress not found in /var/www/html - copying now...
wordpress_1  | Complete! WordPress has been successfully copied to /var/www/html
wordpress_1  | [06-Jan-2021 09:19:37 UTC] PHP Warning:  mysqli::__construct(): (HY000/2002): Connection refused in Standard input code on line 22
wordpress_1  | 
wordpress_1  | MySQL Connection Error: (2002) Connection refused
wordpress_1  | 
wordpress_1  | MySQL Connection Error: (2002) Connection refused
wordpress_1  | 
wordpress_1  | MySQL Connection Error: (2002) Connection refused
wordpress_1  | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.19.0.3. Set the 'ServerName' directive globally to suppress this message
wordpress_1  | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.19.0.3. Set the 'ServerName' directive globally to suppress this message
wordpress_1  | [Wed Jan 06 09:19:46.171484 2021] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.38 (Debian) PHP/7.4.13 configured -- resuming normal operations
wordpress_1  | [Wed Jan 06 09:19:46.171532 2021] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
```

> Docker-compose up：
>
> 这将以分离模式运行 Docker-compose up，获取所需的 Docker 映像，并启动 wordpress 和数据库容器。

> docker-compose up -d:后台启动

![image-20210106174126422](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230101.png)

> docker-compose up --build:重新构建

5.测试访问

http://IP:8000/

![image-20210106172753760](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230102.png)

> 如果你正在使用 Docker MACHINE，你可以运行命令 Docker-MACHINE ip MACHINE _ vm 来获取机器地址，然后在 web 浏览器中打开 http://machine_vm_ip:8000。

![image-20210106173803639](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230103.png)

> dockerfile:构建镜像。
>
> docker-compose.yaml:定义多个容器一键启动所有容器。定义多个容器一键启动所有容器。

# Docker Swarm

## 环境搭建

准备4台虚拟机，配置好网络，可以访问外网。

4台服务器执行如下命令安装Docker。

1.安装gcc相关环境

```
yum -y install gcc
yum -y install gcc-c++
```

2.卸载旧版本

```shell
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

3.安装基础包

```shell
yum install -y yum-utils
```

4.添加镜像仓库

```shell
默认国外源：
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
阿里云：    
yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

5.更新yum软件包索引

```shell
yum makecache fast
```

6.安装 Docker引擎

```shell
yum install -y docker-ce docker-ce-cli containerd.io
```

7.启动并加入开机自启动

```shell
systemctl start docker
systemctl enable docker
```

判断是否安装成功：

```shell
[root@localhost ~]# docker version
Client: Docker Engine - Community
 Version:           **19.03.13**
 API version:       1.40
 Go version:        **go1.13.15**
 Git commit:        4484c46d9d
 Built:             Wed Sep 16 17:03:45 2020
 OS/Arch:           linux/amd64
 Experimental:      false

**Server: Docker Engine - Community**
 Engine:
  Version:          19.03.13
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.13.15
  Git commit:       4484c46d9d
  Built:            Wed Sep 16 17:02:21 2020
  OS/Arch:          **linux/amd64**
  Experimental:     false
 containerd:
  Version:          1.3.7
  GitCommit:        8fba4e9a7d01810a393d5d25a3621dc101981175
 runc:
  Version:          1.0.0-rc10
  GitCommit:        dc9208a3303feef5b3839f4323d9beb36df0a9dd
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683
[root@localhost ~]# 
```

8.配置镜像加速器

针对Docker客户端版本大于 1.10.0 的用户

您可以通过修改daemon配置文件/etc/docker/daemon.json来使用加速器

```shell
sudo mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://gnxq79wc.mirror.aliyuncs.com"]
}
EOF

sudo systemctl daemon-reload

sudo systemctl restart docker
```

## Swarm集群搭建

文档：https://docs.docker.com/get-started/swarm-deploy/

![image-20210107172518483](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230104.png)

Swarm概述：

要在群模式下使用 Docker，请安装 Docker。

当前版本的 Docker 包括Swarm模型，用于管理一组称为Swarm模型的 Docker 引擎。使用 dockercli 创建一个群体，将应用服务部署到一个群体，并管理群体行为。

特点：

1.集群管理与 Docker 引擎集成，不需要额外的编排软件来创建或管理群。

2.分散式设计master与worker

3.声明性服务模型: Docker Engine 使用声明性方法来定义应用程序堆栈中各种服务的期望状态。例如，您可以描述一个应用程序，该应用程序由具有消息排队服务和数据库后端的 web 前端服务组成。

4.伸缩性: 对于每个服务，您可以声明想要执行的任务的数量。当你向上或向下扩展时，群管理器会通过添加或删除任务来自动调整以保持所需的状态。

5.状态协调: 群管理器节点不断监视集群状态，并协调实际状态和您所需的状态之间的任何差异。例如，如果您设置了一个服务来运行一个容器的10个副本，并且一个工作机器承载了其中的两个副本崩溃，那么管理器将创建两个新的副本来替换崩溃的副本。管理器将新的副本分配给所有能够执行任务的工作者。

6.多主机网络: 可以为您的服务指定overlay网络。当初始化或更新应用程序时，Swarm manager会自动为overlay网络上的容器分配地址。

7.服务发现: Swarm manager 节点为群中的每个服务分配唯一的 DNS 名称和运行容器的负载平衡。你可以通过嵌入在群体中的 DNS 服务器查询群体中运行的每个容器。

8.负载均衡: 实现服务副本负载均衡，提供入口访问。也可以将服务入口暴露给外部负载均衡器再次负载均衡。

9.安全传输: 群中的每个节点都强制使用TLS 相互认证和加密，以确保自身和其他节点之间的通信安全。您可以选择使用来自自定义根 CA 的自签名根证书或证书。

10.滚动更新: 在升级时，逐步将应用更新到新的节点。Swarm允许您控制不同节点集的服务部署之间的延迟。如果出现任何问题，您可以回滚到该服务的以前版本。

## 工作模式

节点是如何工作的?

Docker Engine 1.12引入了集群模式，使您能够创建一个由一个或多个 Docker Engine 组成的集群，称为Swarm。一个集群由一个或多个节点组成: 在集群模式下运行 Docker Engine 1.12或更高版本的物理或虚拟机器。

节点有两种类型: [**managers**](https://docs.docker.com/engine/swarm/how-swarm-mode-works/nodes/#manager-nodes) and [**workers**](https://docs.docker.com/engine/swarm/how-swarm-mode-works/nodes/#worker-nodes).

![Swarm mode cluster](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230105.png)

Manager nodes（管理器节点）

管理器节点处理集群管理任务:

- maintaining cluster state 保持集群状态
- scheduling services 调度服务
- serving swarm mode 服务群模式
- Raft一致性算法（保证可用性）

- 管理者集群最多只能忍受损失`(N-1)/2` managers. 

  建议一个集群最少有3台主机。

  建议一个集群最多有七个管理器节点。

  > 重要提示: 添加更多的管理器并不意味着增加可伸缩性或更高的性能。

Worker nodes （工作节点）

工作节点也是 Docker Engine 的实例，它的唯一目的是执行容器。工作节点不参与 Raft 分布式状态，不做调度决策，也不服务于集群模式的 HTTP API。

您可以创建一个由一个管理器节点组成的群，但是如果没有至少一个管理器节点，就不能有一个worker节点。默认情况下，所有的管理者都是worker。在单个管理器节点集群中，您可以运行诸如 docker 服务 create 之类的命令，调度程序将所有任务放在本地引擎上。

若要防止调度程序将任务放在多节点群中的管理器节点上，请将管理器节点的可用性设置为 Drain。调度程序在 Drain 模式下正常停止节点上的任务，并在活动节点上调度任务。调度程序不会将新任务分配给具有 Drain 可用性的节点

服务是如何运作的？

要在 Docker Engine 处于群模式时部署应用程序映像，需要创建一个服务。服务通常是某个较大应用程序上下文中微服务的映像。服务的示例可能包括 HTTP 服务器、数据库或希望在分布式环境中运行的任何其他类型的可执行程序。

Services：

当您将服务部署到Swarm时，Swarm manager接受您的服务定义作为服务的期望状态。然后将Swarm中节点上的服务作为一个或多个副本任务进行调度。这些任务在群中的节点上独立运行。

例如，假设您希望在一个 HTTP 侦听器的三个实例之间进行负载平衡。下图显示了一个具有三个副本的 HTTP 侦听器服务。监听器的三个实例中的每一个都是群中的一个任务。

![services diagram](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230106.png)

TASK和Scheduler:

容器是一个独立的过程。在群模式模型中，每个任务只调用一个容器。任务类似于调度程序放置容器的“槽”。一旦容器处于激活状态，调度程序就会识别出任务处于运行状态。如果容器未能通过健康检查或终止，则任务终止。

任务是集群中调度的原子单位。当您通过创建或更新服务来声明所需的服务状态时，协调器通过调度任务来实现所需的状态。例如，您定义了一个服务，它指示协调器始终运行 HTTP 侦听器的三个实例。协调者通过创建三个任务来进行响应。每个任务都是调度程序通过生成容器填充的槽。容器是任务的实例化。如果 HTTP 侦听器任务随后失败或崩溃，协调器将创建一个产生新容器的新副本任务。

任务是一种单向机制。它通过一系列的状态单调地进行: 分配、准备、运行等等。如果任务失败，协调器将删除任务及其容器，然后根据服务指定的所需状态创建一个新任务来替换它。

Docker 群模式的基本逻辑是一个通用的调度器和协调器。服务和任务抽象本身并不知道它们实现的容器。假设，您可以实现其他类型的任务，例如虚拟机任务或非容器化的流程任务。调度程序和协调器对任务的类型不知道。但是，当前版本的 Docker 只支持容器任务。

下图显示了群模式如何接受服务创建请求并将任务调度到工作节点。

![services flow](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230107.png)

命令—管理—API—调度—工作节点（创建TASK,容器部署，维护）

eplicated and global services:

有两种类型的服务部署，复制的和全局的。

对于复制服务，指定要运行的相同任务的数量。例如，您决定使用三个副本部署一个 HTTP 服务，每个副本提供相同的内容。

全局服务是在每个节点上运行一个任务的服务。没有预先指定的任务数量。每次向群中添加一个节点时，协调器创建一个任务，调度器将任务分配给新节点。全球服务的优秀候选者是监控代理程序、反病毒扫描程序或其他类型的容器，您希望在群中的每个节点上运行这些容器。

下图显示了一个黄色的三服务副本和一个灰色的全局服务。

![global vs replicated services](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230108.png)

解释Replicated and global ：

Replicated 复制：指定要运行的节点和数量，默认。

global 全局：在每个节点上运行一个任务的服务。每增加一个新节点，协调器将创建一个新的任务，调度器再将任务分配给新节点。

具体方法：

```
--mode string
Service mode (replicated or global)(default "replicated")

docker service create --mode replicated --name mytom tomcat:7 默认

docker service create --mode global --name mytest alpine ping baidu.com

场景？
日志收集
每一个节点都有自己的日志收集器，过滤，把所有日志最终再传给日志中心服务监控状态性能。
```



## 使用Swarm

1.docker swarm --help

```
[root@localhost ~]# docker swarm --help

Usage:  docker swarm COMMAND

Manage Swarm

Commands:
  ca          Display and rotate the root CA
  init        Initialize a swarm        初始化一个集群
  join        Join a swarm as a node and/or manager   加入一个集群
  join-token  Manage join tokens     创建一个token
  leave       Leave the swarm     离开一个集群
  unlock      Unlock swarm
  unlock-key  Manage the unlock key
  update      Update the swarm    更新一个集群

Run 'docker swarm COMMAND --help' for more information on a command.
[root@localhost ~]#
```

2.docker swarm init --help

```
[root@localhost ~]# docker swarm init --help

Usage:  docker swarm init [OPTIONS]

Initialize a swarm

Options:
      --advertise-addr string    增加广播地址    Advertised address (format: <ip|interface>[:port])
      --autolock                               Enable manager autolocking (requiring an
                                               unlock key to start a stopped manager)
      --availability string                    Availability of the node
                                               ("active"|"pause"|"drain") (default "active")
      --cert-expiry duration                   Validity period for node certificates
                                               (ns|us|ms|s|m|h) (default 2160h0m0s)
      --data-path-addr string                  Address or interface to use for data path
                                               traffic (format: <ip|interface>)
      --data-path-port uint32                  Port number to use for data path traffic
                                               (1024 - 49151). If no value is set or is set
                                               to 0, the default port (4789) is used.
      --default-addr-pool ipNetSlice           default address pool in CIDR format (default [])
      --default-addr-pool-mask-length uint32   default address pool subnet mask length
                                               (default 24)
      --dispatcher-heartbeat duration          Dispatcher heartbeat period (ns|us|ms|s|m|h)
                                               (default 5s)
      --external-ca external-ca                Specifications of one or more certificate
                                               signing endpoints
      --force-new-cluster                      Force create a new cluster from current state
      --listen-addr node-addr                  Listen address (format:
                                               <ip|interface>[:port]) (default 0.0.0.0:2377)
      --max-snapshots uint                     Number of additional Raft snapshots to retain
      --snapshot-interval uint                 Number of log entries between Raft snapshots
                                               (default 10000)
      --task-history-limit int                 Task history retention limit (default 5)
[root@localhost ~]#
```

> --advertise-addr string广播地址

## 初始化

1.查看主机IP信息

```
[root@localhost ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:0c:29:4c:20:77 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.103/24 brd 192.168.100.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::5ff3:633c:1e91:e523/64 scope link tentative noprefixroute dadfailed 
       valid_lft forever preferred_lft forever
    inet6 fe80::4cb8:b4bd:811f:6064/64 scope link tentative noprefixroute dadfailed 
       valid_lft forever preferred_lft forever
    inet6 fe80::da97:34b6:c534:91b8/64 scope link tentative noprefixroute dadfailed 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:e7:a7:1e:81 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
[root@localhost ~]#
```

2.让该主机成为主节点

```
docker swarm init --advertise-addr 192.168.100.100
```

```
[root@localhost ~]# docker swarm init --advertise-addr 192.168.100.100
Swarm initialized: current node (28fgw2e0nmc14greycbow7v9s) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-303dpxlqb9vehlo7sox0wv56a 192.168.100.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

[root@localhost ~]#
```

3.得到信息

当前节点（28fgw2e0nmc14greycbow7v9s）已加入到Swarm中，现在是一个管理员。

```
Swarm initialized: current node (28fgw2e0nmc14greycbow7v9s) is now a manager.
```

要将worker工作节点添加到该群集，请运行以下命令

```
docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-303dpxlqb9vehlo7sox0wv56a 192.168.100.100:2377
```

要将管理器添加到该集群，请运行“ docker swarm join-token manager”并按照说明进行操作。

```
To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

> docker swarm init 初始化节点
>
> docker swarm join 加入一个节点

> 获取令牌：
>
> docker swarm join-token manager 生成主节点令牌
>
> docker swarm join-token worker     生成加入节点令牌
>
> 在主节点执行命令后会生成加入命令。

## 加入集群

在工作节点执行加入集群命令：

```
docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-303dpxlqb9vehlo7sox0wv56a 192.168.100.100:2377
```

结果：此节点作为工作节点已加入集群。

```
[root@localhost ~]# docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-303dpxlqb9vehlo7sox0wv56a 192.168.100.100:2377
This node joined a swarm as a worker.
[root@localhost ~]# 
```

查看加入的节点信息

在主节点执行如下命令:

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
28fgw2e0nmc14greycbow7v9s *   localhost.localdomain   Ready     Active         Leader           20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

状态：Ready    Active

> 主节点默认有Leader标签。工作节点无。

将所有节点加入集群后再查看节点信息

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
28fgw2e0nmc14greycbow7v9s *   localhost.localdomain   Ready     Active         Leader           20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Ready     Active                          20.10.2
syy3uuajc0dwpbsf9n3fevpqz     localhost.localdomain   Ready     Active                          20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

## 删除节点

```
Error response from daemon: This node is already part of a swarm. Use "docker swarm leave" to leave this swarm and join another one.
[root@localhost ~]# docker swarm leave
Node left the swarm.
[root@localhost ~]#
```

将第四台主机改为主节点

从集群中移除后，在主节点上执行docker swarm join-token manager将该管理节点加入集群。

```
[root@localhost ~]# docker swarm join-token manager
To add a manager to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-bdcobfl71betmca8g1aci3hks 192.168.100.100:2377

[root@localhost ~]#
```

生成加入令牌后在第4台主机执行该命令。

```
[root@localhost ~]# docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-bdcobfl71betmca8g1aci3hks 192.168.100.100:2377
This node joined a swarm as a manager.
[root@localhost ~]#
```

再次到主节点查看集群的节点信息

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
0rqyc7d4s43xw8d74iss5exnj     localhost.localdomain   Down      Active                          20.10.2
28fgw2e0nmc14greycbow7v9s *   localhost.localdomain   Ready     Active         Leader           20.10.2
653jropyn5jpg6f1ytwye2xrr     localhost.localdomain   Ready     Active         Reachable        20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Ready     Active                          20.10.2

```

> 加入的管理节点带有Reachable标签。

双主双从集群搭建完毕。

## Raft一致性协议

实验

双主双从：假设一个节点挂掉，其他节点是否可用？

停掉docker-1,在docker-4上执行命令测试

docker-1

```
systemctl stop docker
```

docker-4

```
docker node ls
```

报错信息（来自守护程序的错误响应：rpc错误：）：

```
[root@localhost ~]# docker node ls
Error response from daemon: rpc error: code = DeadlineExceeded desc = context deadline exceeded
[root@localhost ~]#
```

再次启动docker-1主节点，查看节点信息，可以继续工作

发现：

一个主节点挂掉，再次启动后该主节点变为工作节点

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
0rqyc7d4s43xw8d74iss5exnj     localhost.localdomain   Down      Active                          20.10.2
28fgw2e0nmc14greycbow7v9s *   localhost.localdomain   Ready     Active         Reachable        20.10.2
653jropyn5jpg6f1ytwye2xrr     localhost.localdomain   Unknown   Active         Leader           20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Unknown   Active                          20.10.2
syy3uuajc0dwpbsf9n3fevpqz     localhost.localdomain   Down      Active                          20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

![image-20210108143317815](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230109.png)

到docker-4节点查看信息，此时docker-4管理节点变为Leader管理节点。

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
0rqyc7d4s43xw8d74iss5exnj     localhost.localdomain   Down      Active                          20.10.2
28fgw2e0nmc14greycbow7v9s     localhost.localdomain   Ready     Active         Reachable        20.10.2
653jropyn5jpg6f1ytwye2xrr *   localhost.localdomain   Ready     Active         Leader           20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Ready     Active                          20.10.2
syy3uuajc0dwpbsf9n3fevpqz     localhost.localdomain   Down      Active                          20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

![image-20210108143613530](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230110.png)

## 三主节点

实验

将docker-3从集群中删除，由worker节点修改为manager节点。

```
[root@localhost ~]# docker swarm leave
Node left the swarm.
[root@localhost ~]# docker swarm leave
Error response from daemon: This node is not part of a swarm
[root@localhost ~]#
```

manager节点查看节点信息

移除节点后再查看节点会变成Dowm状态。

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
0rqyc7d4s43xw8d74iss5exnj     localhost.localdomain   Down      Active                          20.10.2
28fgw2e0nmc14greycbow7v9s     localhost.localdomain   Ready     Active         Reachable        20.10.2
653jropyn5jpg6f1ytwye2xrr *   localhost.localdomain   Ready     Active         Leader           20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Down      Active                          20.10.2
syy3uuajc0dwpbsf9n3fevpqz     localhost.localdomain   Down      Active                          20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

管理节点生成令牌

```
[root@localhost ~]# docker swarm join-token manager
To add a manager to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-bdcobfl71betmca8g1aci3hks 192.168.100.103:2377

[root@localhost ~]#
```

将docker-3以管理节点加入Swarm集群

```
[root@localhost ~]# docker swarm leave
Error response from daemon: This node is not part of a swarm
[root@localhost ~]# docker swarm join --token SWMTKN-1-5v9a5z3i4fhtiodfho92en7rl9lxowxnz8nbvct9mhqs2843uh-bdcobfl71betmca8g1aci3hks 192.168.100.103:2377
This node joined a swarm as a manager.
[root@localhost ~]#
```

docker-3加入管理节点后在docker-3下执行docker node ls,该节点也被打上Reachable标签。

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
0rqyc7d4s43xw8d74iss5exnj     localhost.localdomain   Down      Active                          20.10.2
28fgw2e0nmc14greycbow7v9s     localhost.localdomain   Ready     Active         Reachable        20.10.2
653jropyn5jpg6f1ytwye2xrr     localhost.localdomain   Ready     Active         Leader           20.10.2
j8xhfzomjxqqq9m97n3rf0xk8 *   localhost.localdomain   Ready     Active         Reachable        20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Down      Active                          20.10.2
syy3uuajc0dwpbsf9n3fevpqz     localhost.localdomain   Down      Active                          20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

worker节点只用来工作，无法操作集群。

 manager管理节点用来操作Swarm集群。

测试关闭docker-1节点

```
[root@localhost ~]# systemctl stop docker 
Warning: Stopping docker.service, but it can still be activated by:
  docker.socket
[root@localhost ~]# 
```

docker-1节点会打上Unreachable（无法到达）标签

```
[root@localhost ~]# docker node ls
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
0rqyc7d4s43xw8d74iss5exnj     localhost.localdomain   Down      Active                          20.10.2
28fgw2e0nmc14greycbow7v9s     localhost.localdomain   Ready     Active         Unreachable      20.10.2
653jropyn5jpg6f1ytwye2xrr *   localhost.localdomain   Ready     Active         Leader           20.10.2
j8xhfzomjxqqq9m97n3rf0xk8     localhost.localdomain   Ready     Active         Reachable        20.10.2
p6q951nif6cweywut097i1ex9     localhost.localdomain   Down      Active                          20.10.2
syy3uuajc0dwpbsf9n3fevpqz     localhost.localdomain   Down      Active                          20.10.2
t1bastpik0mmtzartwvm4o8u4     localhost.localdomain   Ready     Active                          20.10.2
[root@localhost ~]#
```

> 三主一从，挂掉1台管理节点，其他2台管理节点docker-3 docker-4管理节点可以正常使用。

测试挂掉2台管理节点

再停掉1台管理节点docker-3,测试只剩docker-4管理节点是否可用。

docker-3

```
[root@localhost ~]# systemctl stop docker
Warning: Stopping docker.service, but it can still be activated by:
  docker.socket
[root@localhost ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@localhost ~]#
```

docker-4管理节点:无法使用

```
[root@localhost ~]# docker node ls
Error response from daemon: rpc error: code = Unknown desc = The swarm does not have a leader. It's possible that too few managers are online. Make sure more than half of the managers are online.
[root@localhost ~]#
```

> 集群可用：至少保证>3节点，>1台管理节点存活。
>
> Raft协议:保证大多数节点存活才可以用，高可用。

## 弹性扩缩容

docker run 容器启动，不具备扩缩容器！

docker service 具有扩缩容，滚动更新！

```
[root@docker1 ~]# docker service --help

Usage:  docker service COMMAND

Manage services

Commands:
  create      Create a new service
  inspect     Display detailed information on one or more services
  logs        Fetch the logs of a service or task
  ls          List services
  ps          List the tasks of one or more services
  rm          Remove one or more services
  rollback    Revert changes to a service's configuration
  scale       Scale one or multiple replicated services
  update      Update a service

Run 'docker service COMMAND --help' for more information on a command.
[root@docker1 ~]#
```

rollback    Revert changes to a service's configuration（将更改还原到服务的配置）—回滚
  scale       Scale one or multiple replicated services（扩展一个或多个服务）—动态扩缩容
  update      Update a service（更新服务）—更新

创建服务—动态扩展服务—动态更新服务

create帮助命令

```
[root@docker1 ~]# docker service create --help

Usage:  docker service create [OPTIONS] IMAGE [COMMAND] [ARG...]

Create a new service

Options:
      --cap-add list                       Add Linux capabilities
      --cap-drop list                      Drop Linux capabilities
      --config config                      Specify configurations to expose to the service
      --constraint list                    Placement constraints
      --container-label list               Container labels
      --credential-spec credential-spec    Credential spec for managed service account
                                           (Windows only)
  -d, --detach                             Exit immediately instead of waiting for the
                                           service to converge
      --dns list                           Set custom DNS servers
      --dns-option list                    Set DNS options
      --dns-search list                    Set custom DNS search domains
      --endpoint-mode string               Endpoint mode (vip or dnsrr) (default "vip")
      --entrypoint command                 Overwrite the default ENTRYPOINT of the image
  -e, --env list                           Set environment variables
      --env-file list                      Read in a file of environment variables
      --generic-resource list              User defined resources
      --group list                         Set one or more supplementary user groups for the
                                           container
      --health-cmd string                  Command to run to check health
      --health-interval duration           Time between running the check (ms|s|m|h)
      --health-retries int                 Consecutive failures needed to report unhealthy
      --health-start-period duration       Start period for the container to initialize
                                           before counting retries towards unstable (ms|s|m|h)
      --health-timeout duration            Maximum time to allow one check to run (ms|s|m|h)
      --host list                          Set one or more custom host-to-IP mappings (host:ip)
      --hostname string                    Container hostname
      --init                               Use an init inside each service container to
                                           forward signals and reap processes
      --isolation string                   Service container isolation mode
  -l, --label list                         Service labels
      --limit-cpu decimal                  Limit CPUs
      --limit-memory bytes                 Limit Memory
      --limit-pids int                     Limit maximum number of processes (default 0 =
                                           unlimited)
      --log-driver string                  Logging driver for service
      --log-opt list                       Logging driver options
      --max-concurrent uint                Number of job tasks to run concurrently (default
                                           equal to --replicas)
      --mode string                        Service mode (replicated, global, replicated-job,
                                           or global-job) (default "replicated")
      --mount mount                        Attach a filesystem mount to the service
      --name string                        Service name
      --network network                    Network attachments
      --no-healthcheck                     Disable any container-specified HEALTHCHECK
      --no-resolve-image                   Do not query the registry to resolve image digest
                                           and supported platforms
      --placement-pref pref                Add a placement preference
  -p, --publish port                       Publish a port as a node port
  -q, --quiet                              Suppress progress output
      --read-only                          Mount the container's root filesystem as read only
      --replicas uint                      Number of tasks
      --replicas-max-per-node uint         Maximum number of tasks per node (default 0 =
                                           unlimited)
      --reserve-cpu decimal                Reserve CPUs
      --reserve-memory bytes               Reserve Memory
      --restart-condition string           Restart when condition is met
                                           ("none"|"on-failure"|"any") (default "any")
      --restart-delay duration             Delay between restart attempts (ns|us|ms|s|m|h)
                                           (default 5s)
      --restart-max-attempts uint          Maximum number of restarts before giving up
      --restart-window duration            Window used to evaluate the restart policy
                                           (ns|us|ms|s|m|h)
      --rollback-delay duration            Delay between task rollbacks (ns|us|ms|s|m|h)
                                           (default 0s)
      --rollback-failure-action string     Action on rollback failure ("pause"|"continue")
                                           (default "pause")
      --rollback-max-failure-ratio float   Failure rate to tolerate during a rollback (default 0)
      --rollback-monitor duration          Duration after each task rollback to monitor for
                                           failure (ns|us|ms|s|m|h) (default 5s)
      --rollback-order string              Rollback order ("start-first"|"stop-first")
                                           (default "stop-first")
      --rollback-parallelism uint          Maximum number of tasks rolled back
                                           simultaneously (0 to roll back all at once)
                                           (default 1)
      --secret secret                      Specify secrets to expose to the service
      --stop-grace-period duration         Time to wait before force killing a container
                                           (ns|us|ms|s|m|h) (default 10s)
      --stop-signal string                 Signal to stop the container
      --sysctl list                        Sysctl options
  -t, --tty                                Allocate a pseudo-TTY
      --ulimit ulimit                      Ulimit options (default [])
      --update-delay duration              Delay between updates (ns|us|ms|s|m|h) (default 0s)
      --update-failure-action string       Action on update failure
                                           ("pause"|"continue"|"rollback") (default "pause")
      --update-max-failure-ratio float     Failure rate to tolerate during an update (default 0)
      --update-monitor duration            Duration after each task update to monitor for
                                           failure (ns|us|ms|s|m|h) (default 5s)
      --update-order string                Update order ("start-first"|"stop-first")
                                           (default "stop-first")
      --update-parallelism uint            Maximum number of tasks updated simultaneously (0
                                           to update all at once) (default 1)
  -u, --user string                        Username or UID (format: <name|uid>[:<group|gid>])
      --with-registry-auth                 Send registry authentication details to swarm agents
  -w, --workdir string                     Working directory inside the container
[root@docker1 ~]#
```

1.创建服务

```
[root@docker1 ~]# docker service create -p 8888:80 --name my-nginx nginx
t99km76mvfkrfx274gdopaux5
overall progress: 1 out of 1 tasks 
1/1: running   
verify: Service converged 
[root@docker1 ~]#
```

2.查看创建的服务

REPLICAS:副本为1

```
[root@docker1 ~]# docker service ls
ID             NAME       MODE         REPLICAS   IMAGE          PORTS
t99km76mvfkr   my-nginx   replicated   1/1        nginx:latest   *:8888->80/tcp
[root@docker1 ~]#
```

3.查看运行的服务

```
[root@docker1 ~]# docker service ps my-nginx
ID             NAME         IMAGE          NODE      DESIRED STATE   CURRENT STATE           ERROR     PORTS
af2fbra1lyjx   my-nginx.1   nginx:latest   docker4   Running         Running 4 minutes ago             
[root@docker1 ~]#
```

在docker1创建的服务跑在docker4上

NODE：docker4

```
[root@docker4 ~]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS     NAMES
4b56584f6710   nginx:latest   "/docker-entrypoint.…"   10 minutes ago   Up 10 minutes   80/tcp    my-nginx.1.af2fbra1lyjxxmjor5821c4av
[root@docker4 ~]# 
```

4.查看服务详细信息

```
[root@docker1 ~]# docker service inspect my-nginx
[
    {
        "ID": "t99km76mvfkrfx274gdopaux5",
        "Version": {
            "Index": 78
        },
        "CreatedAt": "2021-01-11T02:35:51.137685495Z",
        "UpdatedAt": "2021-01-11T02:35:51.287333784Z",
        "Spec": {
            "Name": "my-nginx",
            "Labels": {},
            "TaskTemplate": {
                "ContainerSpec": {
                    "Image": "nginx:latest@sha256:4cf620a5c81390ee209398ecc18e5fb9dd0f5155cd82adcbae532fec94006fb9",
                    "Init": false,
                    "StopGracePeriod": 10000000000,
                    "DNSConfig": {},
                    "Isolation": "default"
                },
                "Resources": {
                    "Limits": {},
                    "Reservations": {}
                },
                "RestartPolicy": {
                    "Condition": "any",
                    "Delay": 5000000000,
                    "MaxAttempts": 0
                },
                "Placement": {
                    "Platforms": [
                        {
                            "Architecture": "amd64",
                            "OS": "linux"
                        },
                        {
                            "OS": "linux"
                        },
                        {
                            "OS": "linux"
                        },
                        {
                            "Architecture": "arm64",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "386",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "mips64le",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "ppc64le",
                            "OS": "linux"
                        },
                        {
                            "Architecture": "s390x",
                            "OS": "linux"
                        }
                    ]
                },
                "ForceUpdate": 0,
                "Runtime": "container"
            },
            "Mode": {
                "Replicated": {
                    "Replicas": 1
                }
            },
            "UpdateConfig": {
                "Parallelism": 1,
                "FailureAction": "pause",
                "Monitor": 5000000000,
                "MaxFailureRatio": 0,
                "Order": "stop-first"
            },
            "RollbackConfig": {
                "Parallelism": 1,
                "FailureAction": "pause",
                "Monitor": 5000000000,
                "MaxFailureRatio": 0,
                "Order": "stop-first"
            },
            "EndpointSpec": {
                "Mode": "vip",
                "Ports": [
                    {
                        "Protocol": "tcp",
                        "TargetPort": 80,
                        "PublishedPort": 8888,
                        "PublishMode": "ingress"
                    }
                ]
            }
        },
        "Endpoint": {
            "Spec": {
                "Mode": "vip",
                "Ports": [
                    {
                        "Protocol": "tcp",
                        "TargetPort": 80,
                        "PublishedPort": 8888,
                        "PublishMode": "ingress"
                    }
                ]
            },
            "Ports": [
                {
                    "Protocol": "tcp",
                    "TargetPort": 80,
                    "PublishedPort": 8888,
                    "PublishMode": "ingress"
                }
            ],
            "VirtualIPs": [
                {
                    "NetworkID": "y06qj1nd1ebb7k2hfvdvkbepy",
                    "Addr": "10.0.0.9/24"
                }
            ]
        }
    }
]
[root@docker1 ~]#
```

## 网络模式

"PublishMode": 

ingress:默认（特殊的Overlay网络，具备负载均衡的功能：IPVS/VIP）

Overlay:跨服务器网络

Swarm采用Overlay模式

```
[root@docker1 ~]# docker network ls
NETWORK ID     NAME              DRIVER    SCOPE
c155108e2db2   bridge            bridge    local
72827bba54c0   docker_gwbridge   bridge    local
b4006bd11662   host              host      local
y06qj1nd1ebb   ingress           overlay   swarm
44f671135a58   none              null      local
[root@docker1 ~]#
```

查看详细信息

```
[root@docker1 ~]# docker network inspect ingress
[
    {
        "Name": "ingress",
        "Id": "y06qj1nd1ebb7k2hfvdvkbepy",
        "Created": "2021-01-08T03:47:18.963091326-05:00",
        "Scope": "swarm",
        "Driver": "overlay",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "10.0.0.0/24",
                    "Gateway": "10.0.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": true,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "ingress-sbox": {
                "Name": "ingress-endpoint",
                "EndpointID": "0d906a438633c47c060ff4c83c057f45d56e47887679d6777c0342cee98a4201",
                "MacAddress": "02:42:0a:00:00:02",
                "IPv4Address": "10.0.0.2/24",
                "IPv6Address": ""
            }
        },
        "Options": {
            "com.docker.network.driver.overlay.vxlanid_list": "4096"
        },
        "Labels": {},
        "Peers": [
            {
                "Name": "30f2fbbc3dfd",
                "IP": "192.168.100.100"
            },
            {
                "Name": "a77efb0227b7",
                "IP": "192.168.100.101"
            },
            {
                "Name": "30078eb13cab",
                "IP": "192.168.100.103"
            },
            {
                "Name": "79e62e9699f5",
                "IP": "192.168.100.102"
            }
        ]
    }
]
[root@docker1 ~]#
```

 "Peers": [
            {
                "Name": "30f2fbbc3dfd",
                "IP": "192.168.100.100"
            },
            {
                "Name": "a77efb0227b7",
                "IP": "192.168.100.101"
            },
            {
                "Name": "30078eb13cab",
                "IP": "192.168.100.103"
            },
            {
                "Name": "79e62e9699f5",
                "IP": "192.168.100.102"
            }

ingress：其实是绑定了4台主机的网络信息。

虽然docker在4台主机上，实际网络是同一个！ingress是一个特殊的Overlay网络。

不同节点的IP是不同的，节点之间的网络是无法通信的，通过Overlay网络可以打通节点间的访问。

访问增大，增加副本缓解服务器压力。

update帮助命令

--replicas uint                      Number of tasks创建任务数（副本）

```
[root@docker1 ~]# docker service update --help

Usage:  docker service update [OPTIONS] SERVICE

Update a service

Options:
      --args command                       Service command args
      --cap-add list                       Add Linux capabilities
      --cap-drop list                      Drop Linux capabilities
      --config-add config                  Add or update a config file on a service
      --config-rm list                     Remove a configuration file
      --constraint-add list                Add or update a placement constraint
      --constraint-rm list                 Remove a constraint
      --container-label-add list           Add or update a container label
      --container-label-rm list            Remove a container label by its key
      --credential-spec credential-spec    Credential spec for managed service account
                                           (Windows only)
  -d, --detach                             Exit immediately instead of waiting for the
                                           service to converge
      --dns-add list                       Add or update a custom DNS server
      --dns-option-add list                Add or update a DNS option
      --dns-option-rm list                 Remove a DNS option
      --dns-rm list                        Remove a custom DNS server
      --dns-search-add list                Add or update a custom DNS search domain
      --dns-search-rm list                 Remove a DNS search domain
      --endpoint-mode string               Endpoint mode (vip or dnsrr)
      --entrypoint command                 Overwrite the default ENTRYPOINT of the image
      --env-add list                       Add or update an environment variable
      --env-rm list                        Remove an environment variable
      --force                              Force update even if no changes require it
      --generic-resource-add list          Add a Generic resource
      --generic-resource-rm list           Remove a Generic resource
      --group-add list                     Add an additional supplementary user group to the
                                           container
      --group-rm list                      Remove a previously added supplementary user
                                           group from the container
      --health-cmd string                  Command to run to check health
      --health-interval duration           Time between running the check (ms|s|m|h)
      --health-retries int                 Consecutive failures needed to report unhealthy
      --health-start-period duration       Start period for the container to initialize
                                           before counting retries towards unstable (ms|s|m|h)
      --health-timeout duration            Maximum time to allow one check to run (ms|s|m|h)
      --host-add list                      Add a custom host-to-IP mapping (host:ip)
      --host-rm list                       Remove a custom host-to-IP mapping (host:ip)
      --hostname string                    Container hostname
      --image string                       Service image tag
      --init                               Use an init inside each service container to
                                           forward signals and reap processes
      --isolation string                   Service container isolation mode
      --label-add list                     Add or update a service label
      --label-rm list                      Remove a label by its key
      --limit-cpu decimal                  Limit CPUs
      --limit-memory bytes                 Limit Memory
      --limit-pids int                     Limit maximum number of processes (default 0 =
                                           unlimited)
      --log-driver string                  Logging driver for service
      --log-opt list                       Logging driver options
      --max-concurrent uint                Number of job tasks to run concurrently (default
                                           equal to --replicas)
      --mount-add mount                    Add or update a mount on a service
      --mount-rm list                      Remove a mount by its target path
      --network-add network                Add a network
      --network-rm list                    Remove a network
      --no-healthcheck                     Disable any container-specified HEALTHCHECK
      --no-resolve-image                   Do not query the registry to resolve image digest
                                           and supported platforms
      --placement-pref-add pref            Add a placement preference
      --placement-pref-rm pref             Remove a placement preference
      --publish-add port                   Add or update a published port
      --publish-rm port                    Remove a published port by its target port
  -q, --quiet                              Suppress progress output
      --read-only                          Mount the container's root filesystem as read only
      --replicas uint                      Number of tasks
      --replicas-max-per-node uint         Maximum number of tasks per node (default 0 =
                                           unlimited)
      --reserve-cpu decimal                Reserve CPUs
      --reserve-memory bytes               Reserve Memory
      --restart-condition string           Restart when condition is met
                                           ("none"|"on-failure"|"any")
      --restart-delay duration             Delay between restart attempts (ns|us|ms|s|m|h)
      --restart-max-attempts uint          Maximum number of restarts before giving up
      --restart-window duration            Window used to evaluate the restart policy
                                           (ns|us|ms|s|m|h)
      --rollback                           Rollback to previous specification
      --rollback-delay duration            Delay between task rollbacks (ns|us|ms|s|m|h)
      --rollback-failure-action string     Action on rollback failure ("pause"|"continue")
      --rollback-max-failure-ratio float   Failure rate to tolerate during a rollback
      --rollback-monitor duration          Duration after each task rollback to monitor for
                                           failure (ns|us|ms|s|m|h)
      --rollback-order string              Rollback order ("start-first"|"stop-first")
      --rollback-parallelism uint          Maximum number of tasks rolled back
                                           simultaneously (0 to roll back all at once)
      --secret-add secret                  Add or update a secret on a service
      --secret-rm list                     Remove a secret
      --stop-grace-period duration         Time to wait before force killing a container
                                           (ns|us|ms|s|m|h)
      --stop-signal string                 Signal to stop the container
      --sysctl-add list                    Add or update a Sysctl option
      --sysctl-rm list                     Remove a Sysctl option
  -t, --tty                                Allocate a pseudo-TTY
      --ulimit-add ulimit                  Add or update a ulimit option (default [])
      --ulimit-rm list                     Remove a ulimit option
      --update-delay duration              Delay between updates (ns|us|ms|s|m|h)
      --update-failure-action string       Action on update failure
                                           ("pause"|"continue"|"rollback")
      --update-max-failure-ratio float     Failure rate to tolerate during an update
      --update-monitor duration            Duration after each task update to monitor for
                                           failure (ns|us|ms|s|m|h)
      --update-order string                Update order ("start-first"|"stop-first")
      --update-parallelism uint            Maximum number of tasks updated simultaneously (0
                                           to update all at once)
  -u, --user string                        Username or UID (format: <name|uid>[:<group|gid>])
      --with-registry-auth                 Send registry authentication details to swarm agents
  -w, --workdir string                     Working directory inside the container
[root@docker1 ~]#
```

5.创建3个副本

```
[root@docker1 ~]# docker service update --replicas 3 my-nginx 
my-nginx
overall progress: 3 out of 3 tasks 
1/3: running   
2/3: running   
3/3: running   
verify: Service converged 
[root@docker1 ~]#
```

6.查看创建的副本

创建的副本跑在docker1、docker2、docker4上。

```
[root@docker1 ~]# docker service ps my-nginx
ID             NAME         IMAGE          NODE      DESIRED STATE   CURRENT STATE            ERROR     PORTS
af2fbra1lyjx   my-nginx.1   nginx:latest   docker4   Running         Running 27 minutes ago             
aldb5980l82x   my-nginx.2   nginx:latest   docker2   Running         Running 3 minutes ago              
lx0ylq7q7l5u   my-nginx.3   nginx:latest   docker1   Running         Running 3 minutes ago              
[root@docker1 ~]#
```

docker1

```
[root@docker1 ~]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS     NAMES
12ea2cc33770   nginx:latest   "/docker-entrypoint.…"   5 minutes ago   Up 5 minutes   80/tcp    my-nginx.3.lx0ylq7q7l5ugxj79xqh9seku
[root@docker1 ~]#
```

docker2

```
[root@docker2 ~]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS     NAMES
843c3d3519a4   nginx:latest   "/docker-entrypoint.…"   6 minutes ago   Up 6 minutes   80/tcp    my-nginx.2.aldb5980l82xeh13ik8yax3dq
[root@docker2 ~]#
```

docker4

```
[root@docker4 ~]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS     NAMES
4b56584f6710   nginx:latest   "/docker-entrypoint.…"   30 minutes ago   Up 30 minutes   80/tcp    my-nginx.1.af2fbra1lyjxxmjor5821c4av
[root@docker4 ~]# 
```

docker3上没有

```
[root@docker3 ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@docker3 ~]#
```

7.访问测试

![image-20210111111552772](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230111.png)

docker3没有运行容器，但在集群里面，它的IP依然可以访问nginx项目!

集群中任意节点都可以访问，服务可以有多个副本动态扩缩容实现高可用！

8.一次启动10个副本

```
[root@docker1 ~]# docker service update --replicas 10 my-nginx 
my-nginx
overall progress: 10 out of 10 tasks 
1/10: running   
2/10: running   
3/10: running   
4/10: running   
5/10: running   
6/10: running   
7/10: running   
8/10: running   
9/10: running   
10/10: running   
verify: Service converged 
```

9.查看启动的副本

```
[root@docker1 ~]# docker service ls
ID             NAME       MODE         REPLICAS   IMAGE          PORTS
t99km76mvfkr   my-nginx   replicated   10/10      nginx:latest   *:8888->80/tcp
[root@docker1 ~]#
```

10.缩容，更新到1个副本

```
[root@docker1 ~]# docker service update --replicas 1 my-nginx 
my-nginx
overall progress: 1 out of 1 tasks 
1/1:   
verify: Service converged 
[root@docker1 ~]# docker service ls
ID             NAME       MODE         REPLICAS   IMAGE          PORTS
t99km76mvfkr   my-nginx   replicated   1/1        nginx:latest   *:8888->80/tcp
[root@docker1 ~]#
```

```
[root@docker1 ~]# docker service ls
ID             NAME       MODE         REPLICAS   IMAGE          PORTS
t99km76mvfkr   my-nginx   replicated   1/1        nginx:latest   *:8888->80/tcp
[root@docker1 ~]# docker service ps my-nginx
ID             NAME         IMAGE          NODE      DESIRED STATE   CURRENT STATE          ERROR     PORTS
af2fbra1lyjx   my-nginx.1   nginx:latest   docker4   Running         Running 4 hours ago              
aldb5980l82x   my-nginx.2   nginx:latest   docker2   Shutdown        Shutdown 4 hours ago             
lx0ylq7q7l5u   my-nginx.3   nginx:latest   docker1   Shutdown        Shutdown 4 hours ago             
laaa1qqfcwzg   my-nginx.4   nginx:latest   docker2   Shutdown        Shutdown 4 hours ago             
88eb61egsn6q   my-nginx.7   nginx:latest   docker2   Shutdown        Shutdown 4 hours ago             
kxli7w26dft9   my-nginx.8   nginx:latest   docker1   Shutdown        Shutdown 4 hours ago             
[root@docker1 ~]#
```

弹性扩缩容。

11.扩缩容命令

```
[root@docker1 ~]# docker service scale --help

Usage:  docker service scale SERVICE=REPLICAS [SERVICE=REPLICAS...]

Scale one or multiple replicated services

Options:
  -d, --detach   Exit immediately instead of waiting for the service to converge
[root@docker1 ~]#
```

使用方法：

与更新原理一致

```
[root@docker1 ~]# docker service scale my-nginx=5
my-nginx scaled to 5
overall progress: 5 out of 5 tasks 
1/5: running   
2/5: running   
3/5: running   
4/5: running   
5/5: running   
verify: Service converged 
[root@docker1 ~]#
```

## 移除服务

```
[root@docker1 ~]# docker service --help

Usage:  docker service COMMAND

Manage services

Commands:
  create      Create a new service
  inspect     Display detailed information on one or more services
  logs        Fetch the logs of a service or task
  ls          List services
  ps          List the tasks of one or more services
  rm          Remove one or more services
  rollback    Revert changes to a service's configuration
  scale       Scale one or multiple replicated services
  update      Update a service

Run 'docker service COMMAND --help' for more information on a command.
[root@docker1 ~]#
```

移除my-nginx服务

```
[root@docker1 ~]# docker service rm my-nginx
my-nginx
[root@docker1 ~]# docker service ps
"docker service ps" requires at least 1 argument.
See 'docker service ps --help'.

Usage:  docker service ps [OPTIONS] SERVICE [SERVICE...]

List the tasks of one or more services
[root@docker1 ~]# docker service ls
ID        NAME      MODE      REPLICAS   IMAGE     PORTS
[root@docker1 ~]#
```

## Swarm概念学习

![image-20210111160816359](https://gitee.com/l-wenwu/markdown/raw/master/images/20210112230112.png)

**Swarm**

集群的管理和编排。docker可以初始化一个集群，其他节点可以以管理者或工作者加入集群。

**Node**

就是一个docker节点。多个节点就组成了一个网络集群。

**Service**

服务，可以在管理节点或者工作节点来运行，核心！

**Task**

任务，任务是集群中调度的原子单位。当您通过创建或更新服务来声明所需的服务状态时，协调器通过调度任务来实现所需的状态。

## Docker Stack

Docker-compose:单机部署项目

Docker Stack：集群部署项目

```
#单机
docker-compose up -d wordpress.yaml
#集群
docker stack deploy wordpres.yaml

```

例：

```
version: '3'

services:

  web:
    image: wordpress
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_PASSWORD: root
    networks:
      - my-network
    depends_on:
      - mysql
    deploy:
      mode: replicated
      replicas: 3
      restart_policy:
        condition: on-failure
        delay: 5s
        max_attempts: 3
      update_config:
        parallelism: 1
        delay: 10s

  mysql:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: wordpress
    volumes:
      - mysql-data:/var/lib/mysql
    networks:
      - my-network
    deploy:
      mode: global
      placement:
        constraints:
          - node.role == manager

volumes:
  mysql-data:

networks:
  my-network:
    driver: overlay
```

不同点:

Docker stack会忽略了“构建”指令。 您无法使用stack命令构建新镜像。 它是需要镜像是预先已经构建好的。 所以docker-compose更适合于开发场景。

Docker Stack 部署命令：

- docker stack deploy： 用于根据stack文件部署和更新stack服务
- docker stack ls ：列出swarm集群中所有的stack
- docker stack ps: 列出某个已经部署的stack的相关信息。
- docker stack rm：从swarm集群中移除stack

## Docker Secret

安全，配置密码，证书。

```
[root@docker1 ~]# docker secret --help

Usage:  docker secret COMMAND

Manage Docker secrets

Commands:
  create      Create a secret from a file or STDIN as content
  inspect     Display detailed information on one or more secrets
  ls          List secrets
  rm          Remove one or more secrets

Run 'docker secret COMMAND --help' for more information on a command.
[root@docker1 ~]#
```

## Docker Config

```shell
Usage:  docker config COMMAND

Manage Docker configs

Commands:
  create      Create a config from a file or STDIN
  inspect     Display detailed information on one or more configs
  ls          List configs
  rm          Remove one or more configs

Run 'docker config COMMAND --help' for more information on a command.
[root@docker1 ~]#
```

方法：找全套课程学习案例边学边练先跑起来——查看命令帮助文档--help掌握用法——官方查看文档，对具体的原理和工作方式进行学习。

目标：云原生K8s。

学习内容：

**GO语言**

Docker、K8s、Etcd、谷歌V8引擎都是GO语言开发。

技术开始转向GO方向。

天生的并发语言，效率高。

**Go**（又称 **Golang**）是 [Google](https://baike.baidu.com/item/Google/86964) 的 Robert Griesemer，Rob Pike 及 Ken Thompson 开发的一种[静态](https://baike.baidu.com/item/静态)[强类型](https://baike.baidu.com/item/强类型)、[编译型语言](https://baike.baidu.com/item/编译型语言/9564109)。Go 语言语法与 [C](https://baike.baidu.com/item/C/7252092) 相近，但功能上有：内存安全，[GC](https://baike.baidu.com/item/GC/66426)（垃圾回收），[结构形态](https://baike.baidu.com/item/结构形态/5942010)及 CSP-style [并发计算](https://baike.baidu.com/item/并发计算/9939802)。

**Kubernetes**

云原生。
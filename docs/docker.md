
## 快速开始

``` bash
# 创建容器（gpu + mount）
docker run -itd --gpus all --name <container_name> -v /home/zwx/<dir_name>:/home <image_name> /bin/bash
# 启动容器
docker start <container_name> & docker exec -it <container_name> bash
```

## 安装工具

``` bash
# update !!!
apt update
apt install python python3-pip
```

[docker容器的导入和导出](https://blog.csdn.net/u014078109/article/details/126243823)

[本地windows vscode远程连接服务器docker容器](https://blog.csdn.net/hxx123520/article/details/127527117)

[Linux如何查看端口](https://blog.csdn.net/jiey0407/article/details/126433640)



```bash
# update !!!
apt-get update
# vim
apt install vim
# git
apt install git
# python
apt-get install software-properties-common
apt-get install python3.9 python3-pip
```

### 安装python3.9

``` python
apt-get update

# "software-properties-common" 是一个软件包，该软件包提供了一些常用的工具和功能，用于管理软件源（repositories）和 PPA（Personal Package Archive）。
apt-get install software-properties-common 

# Install py39 from deadsnakes repository
add-apt-repository ppa:deadsnakes/ppa

apt-get install python3.9 python3-pip

```

## docker命令

### 镜像（image）

```bash
# 查看镜像文件
docker images
# 删除镜像文件
docker rmi 镜像文件id
```

### 容器（container）

``` shell
# 查看运行中的容器
docker ps
# 查看所有容器
docker ps -a

# 创建并进入容器(镜像文件名)
docker run -itd image_name /bin/bash
# 启动容器
docker start container_name
# 进入容器（如果从这个容器退出，容器不会停止）
docker exec -it container_name /bin/bash

# 退出容器（停止）
exit
# 退出容器（不停止）
ctrl + P + Q

# 删除容器 (无法删除正在运行的容器，强制删除 rm -f)
docker rm 容器id

# 重新启动容器
docker restart 容器id
# 停止正在运行的容器
docker stop 容器id
# 强制停止正在运行的容器
docker kill 容器id

# 查看更详细的关于某一个容器的信息
docker inspect  容器id/image
```

## 其他操作

### 容器连接

``` shell
# 创建一个 python 应用的容器
# -P :是容器内部端口随机映射到主机的端口
docker run -d -P training/webapp python app.py
# -p : 是容器内部端口绑定到指定的主机端口
docker run -d -p 5000:5000 training/webapp python app.py
# 指定容器绑定的网络地址
docker run -d -p 127.0.0.1:5001:5000 training/webapp python app.py
# 查看端口的绑定情况(adoring_stonebraker为容器名)，输出：127.0.0.1:5001
docker port adoring_stonebraker 5000

# Docker 容器互联
# 创建一个新的 Docker 网络（-d：参数指定 Docker 网络类型，有 bridge、overlay）
docker network create -d bridge test-net
# 查看当前网络
docker network ls
# 运行一个容器并连接到新建的 test-net 网络
docker run -itd --name test1 --network test-net ubuntu /bin/bash
```

### docker中使用nginx镜像布置静态网站

```shell
# 1.导入nginx镜像
[root@docker1 images]# docker load -i nginx.tar
# 2.运行nginx容器
[root@docker1 images]# docker run -it --name  vm1 nginx bash
# 3.容器内设置
root@e0d6fcaf179d:/# cd /usr/share/nginx/html
root@e0d6fcaf179d:/usr/share/nginx/html # echo www.orange_lei.com > index.html 
root@e0d6fcaf179d:/usr/share/nginx/html # cat index.html
# www.orange_lei.com
root@e0d6fcaf179d:/usr/share/nginx/html # cd /usr/sbin/
root@e0d6fcaf179d:/usr/sbin # ./nginx
# 在容器内首先编辑网页html信息，然后启动nginx

# 4.查看nginx容器ip
# 按下ctrl+p然后按ctrl+q就可以将容器打入后台
[root@docker1 images]# docker inspect vm1            ##可以查看具体信息

# 5.测试
[root@docker1 images]# curl 172.17.0.2
# www.orange_lei.com
# 这样一个静态网页就部署好了
```

```shell
# 容器外
docker run -d --name nginx01 -v /home/zwx/volume/nginx:/home -p 20101:80 nginx
docker exec -it nginx01 /bin/bash
# 容器内
cd /usr/share/nginx/html
apt update
apt install vim
vim index.html
nginx
exit

# 查看挂载是否成功
docker inspect nginx01

# 停止和开始
docker stop nginx01
docker start nginx01
docker exec -it nginx01 /bin/bash

# 更改文件
cp /home/index.html /usr/share/nginx/html/index.html
```

### ubuntu_01

```shell
# 安装python
apt update
apt-get install python3
python3 -V
python3
ctrl + D

# 换源
apt-get install vim
vim /etc/apt/sources.list
 # 清华源
 deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
 deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
 deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
 deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
 deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
 deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
 deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
 deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
 deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
 deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
###
apt update

# yolov5
apt install git
git clone https://github.com/ultralytics/yolov5.git
apt install python3-pip
pip3 -V
pip3 install -r requirements.txt
```












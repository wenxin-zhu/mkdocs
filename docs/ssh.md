# ssh

## ssh 远程连接 docker 容器

### 创建和运行容器

```bash
# 创建容器
docker run -itd --gpus all --name <container_name> -p <your_port>:22 -v <host_dir_name>:/home <image_name> /bin/bash
# 启动容器
docker start <container_name> & docker exec -it <container_name> bash
```

### 容器内配置

```bash
# 修改root用户密码(必须要有)
passwd

# 添加用户
apt install sudo
sudo adduser username
sudo vim /etc/sudoers # 在root的下一行添加username的行，退出用:wq!

# 安装ssh
apt update
apt install ssh

# 修改ssh配置文件
vim /etc/ssh/sshd_config  
# 将PasswordAuthentication设置成yes，允许非root用户使用密码远程连接
# （已弃用）将PermitRootLogin 设置为yes  #允许root用户使用ssh登录

# 将公钥放置到远端服务器上，将公钥附加到~/.ssh/authorized_keys中，如cat id_rsa.pub >> ~/.ssh/authorized_keys
# 确保~/.ssh/目录的权限700，~/.ssh/authorized_keys文件的权限是600

# 启动sshd服务
/etc/init.d/ssh restart 
```

### 连接容器

```bash
ip：宿主机ip
端口号：第一步的 <your_port>
用户名：root
密码：passwd设置的密码
```


## ssh免密登录

windows用户目录下的.ssh目录下的id_rsa.pub为公钥

将其上传到需要进行免密登录的用户的主目录下的.ssh文件夹中，并且重命名为authorized_keys，如：`/home/zwx/.ssh/authorized_keys`




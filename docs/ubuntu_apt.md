# ubuntu换源

通常我们使用ubuntu虚拟机的时候总是出现网络过慢导致的更新下载失败等问题

原因：Ubuntu默认的服务器是在国外，自然连接就很慢。

国内有许多可用的镜像源，只需要更改镜像源，就能从国内的镜像源下载你需要的软件、工具等。 推荐使用清华镜像源，如果需要使用其他镜像源可以查询相关镜像官网，并更换对应的镜像源码即可，操作步骤都如下。

下面介绍更换清华镜像源的方法

1.打开Ubuntu的控制台（快捷键ctrl+Alt T）

![img](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5Yaw5bGx5Li25LiA6KeS,size_20,color_FFFFFF,t_70,g_se,x_16.png)

2.进入 /etc/apt/路径

``` bash
cd /etc/apt/
```

3.将sources.list备份保存为sources.backup.list,以防止有需要的时候更换回来

``` bash
cp -a sources.list sources.backup.list
```

4.打开[清华镜像](https://mirrors.tuna.tsinghua.edu.cn/)官方,在搜索框输入ubuntu ,点击ubuntu旁边的小问号

![img](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5Yaw5bGx5Li25LiA6KeS,size_20,color_FFFFFF,t_70,g_se,x_16-16849501606703.png)

 5.根据相应的版本复制镜像源码，查看ubuntu版本

![img](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/b070f8ab61b74615bdb0c8847802f02b.png)

> nx是arm架构，这里要使用ubuntu-ports镜像

查看版本方法： 

``` bash
cat /etc/issue
```

![img](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5Yaw5bGx5Li25LiA6KeS,size_10,color_FFFFFF,t_70,g_se,x_16.png)

这里我的版本号是：21.10，需要在清华网站上选择相应的版本后再复制镜像源码

 6.打开sources.list

``` bash
sudo gedit sources.list
```

7.将sources.list内的内容清空，粘贴刚刚复制的镜像源，并保存（save）

![img](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5Yaw5bGx5Li25LiA6KeS,size_20,color_FFFFFF,t_70,g_se,x_16-168495025259310.png)

8.更新镜像源

``` bash
 sudo apt-get update
```

![img](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5Yaw5bGx5Li25LiA6KeS,size_20,color_FFFFFF,t_70,g_se,x_16-168495027843013.png)



> 转载自[ubuntu更改镜像源](https://blog.csdn.net/qq_57171795/article/details/123109463)
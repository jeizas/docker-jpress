### Docker上部署Jpress，快捷搭建自己的博客系统

#### 一、准备资源文件

- [Jpress](http://jpress.io/)
- [Docker安装](https://yeasy.gitbooks.io/docker_practice/content/install/mac.html)
- [网易蜂巢镜像](https://c.163.com/)

#### 二、编写Dockerfile文件

- FROM <image name> -->所有Dockerfile都必须以FROM命令开始。 FROM命令会指定镜像基于哪个基础镜像创建，接下来的命令也会基于这个基础镜像
- MAINTAINER <author name> -->设置该镜像的作者 
- RUN [command] -->在shell或者exec的环境下执行的命令。RUN指令会在新创建的镜像上添加新的层面，接下来提交的结果用在Dockerfile的下一条指令中
- ADD [src] [destination] -->复制文件指令
- CMD command param1 param2 -->提供了容器默认的执行命令
- ENTRYPOINT command param1 param2 -->配置给容器一个可执行的命令，这意味着在每次使用镜像创建容器时一个特定的应用程序可以被设置为默认程序
- WORKDIR /path/to/workdir -->指定RUN、CMD与ENTRYPOINT命令的工作目录
- ENV <key> <value> -->设置环境变量
- USER <uid> -->镜像正在运行时设置一个UID
- VOLUME ["/data"] -->授权访问从容器内到主机上的目录

#### 三、生成image

```shell
docker build -t jpress:latest [Dockerfile文件路径]
```

#### 四、使用镜像运行容器

```shell
docker run -d -p 8888:8080 jpress
docker exec -it [containId] bash

//数据库安装
docker run --name [name] -e MYSQL_ROOT_PASSWORD=[my-secret-pw] -e MYSQL_DATABASE=[jpress] -d mysql:tag
```

#### 五、浏览器中初始化

+ 访问网站localhsot:8888/jpress 按引导搭建自己的博客系统

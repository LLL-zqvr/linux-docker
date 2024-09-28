# linux-docker

### Introduction
记录一下学习部署的过程和某些步骤中需要注意的地方~

### some useful commands

- `sudo -i` 切换成超级管理员
- `systemctl stop firewalld` 关掉防火墙
- `systemctl start docker` 启动docker
- ` docker images` 查看所有镜像
- cd + 空格 + 目录, 如 ` cd /home/services/mysql`进入指定路径的目录,如这里就是进入mysql目录
- `cd ..`返回上一级目录，另：注意`cd`和`..`间有空格！
- `cd` 回到根目录
- `ls` 查看当前路径下的所有(未隐藏)文件
- `rm 文件名` 删除路径下的指定文件,另：在删除前可以先`ls`一下，按照查出来的信息来删，防止删错
- `rm -r 目录`删除目录
- `docker ps` 查看容器的信息
- `docker logs "947"`另：947是我的容器名称 这里是查看容器日志

### ordinary errors

- ` ✘ public-mysql Error Get "https://registry-1.docker.io/v2/": dial tcp:...                     0.0s`  
  解决方法:修改DNS https://blog.csdn.net/weixin_47316183/article/details/131987609
  

### Update

#### 2024/9/25

#### 2024/9/24

- 端口映射，使用主机127.0.0.1的10022端口映射虚拟机xxx的22端口(ssh的默认端口);
- 创建虚拟机，在软件选择那里选择基础设施服务器，不用有附加选项。
  另：因为是基础设施服务器，一开始安装docker时指令需要自己手敲，一定要留意，要仔细。


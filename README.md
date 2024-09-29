# linux-docker

### Introduction
记录一下学习部署的过程和某些步骤中需要注意的地方~

### some useful commands

- `sudo -i` 切换成超级管理员
- `systemctl stop firewalld` 关掉防火墙
- `systemctl start docker` 启动docker
- `systemctl status docker` 启动docker
- ` docker images` 查看所有镜像
- cd + 空格 + 目录, 如 ` cd /home/services/mysql`进入指定路径的目录,如这里就是进入mysql目录
- `cd ..`返回上一级目录，另：注意`cd`和`..`间有空格！
- `cd` 回到家目录，root目录
- `cd /` 回到根目录
- `pwd` 查看当前完整目录
- `ls` 查看当前路径下的所有(未隐藏)文件
- `ls -a`查看当前目录的所有文件，包括隐藏文件
- `mkdir 目录名`创建一个新目录
- `mkdir -p 目录名1/目录名2/目录名3` 创建多级目录
- `vi 文件名` 修改文件内容(如果没有该文件会先创建出来)
- `rm 文件名` 删除路径下的指定文件,另：在删除前可以先`ls`一下，按照查出来的信息来删，防止删错
- `rm -r 目录`删除目录
- `docker ps` 查看容器的信息
- `docker compose -f docker-compose.yaml up -d` 启动服务容器
- `docker compose ps` 列出项目中的所有容器
- `docker logs b22`另：b22是我的容器名称 这里是查看容器日志
- `docker rename 原名称 现名称`修改容器名称，原名称可以通过`docker ps`查询到
### ordinary errors

- ` ✘ public-mysql Error Get "https://registry-1.docker.io/v2/": dial tcp:...                     0.0s`  
  解决方法:修改DNS https://blog.csdn.net/weixin_47316183/article/details/131987609
  

### Update

#### 2024/9/28

把之前的创建mysql这些的目录都删了，系统地再完成一遍**docker compose部署mysql的过程**。  
部署前准备及须知： 
- docker启动，防火墙啥的都关掉
- 不用再下载docker-compose了，下新的这几个docker版本的时候会把docker compose也一起下了

操作如下：
1. mkdir -p /home/yumu/services/mysql 创建目录，/home/用户名/services/mysql。services下按应用创建目录，即此次要创建的mysql
2. 在mysql下创建docker-compose.yaml文件，另，扩展名可以为yml也可以为yaml， 
它们都是yaml文件的不同扩展名，极大多数情况下没有什么差别。
   (参考博客：https://blog.csdn.net/Ber_Bai/article/details/119989755  )  
  docker-compose.yaml文件内容：https://github.com/bwhyman/linux-docker-examples/blob/master/examples/mysql/docker-compose.yaml
3. 启动容器：docker compose -f docker-compose.yaml up -d
4. 在idea中连接测试。注：端口为主机的端口，这里主机端口多加了10000(端口映射的时候要设置好)，防止和其他任务冲突。
![连接图片](/img/img1.png)
5. 连接好后啥也莫得，在idea创建schema，创建一个简单的user表测试使用
![img2](/img/img2.png)
6. 重命名容器。
7. docker exec -it b22 bash 进入mysql
8. mysql -uroot -p密码 登录mysql
9. show databases; 查看创建的所有数据表
10. use schema_xin; 使用创建的数据库
11. show tables; 查看数据库的数据表
![数据表图片](/img/img3.png)
12. exit; 退出登录
13. exit; 退出数据库，回到终端命令
  

#### 2024/9/24

- 端口映射，使用主机127.0.0.1的10022端口映射虚拟机xxx的22端口(ssh的默认端口);
- 创建虚拟机，在软件选择那里选择基础设施服务器，不用有附加选项。
  另：因为是基础设施服务器，一开始安装docker时指令需要自己手敲，一定要留意，要仔细。


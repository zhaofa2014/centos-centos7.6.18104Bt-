docker仓库地址 https://cloud.docker.com/repository/docker/1872220587/centos

# centos-centos7.6.18104Bt-
centos:centos7.6.1810 安装liunx宝塔面板免费版 5.9.1

docker for Windows centos容器运行宝塔

docker pull centos        //先下载一个docker镜像

//docker run -i -t -d -p 20:20 -p 21:21 -p 80:80 -p 443:443 -p 888:888 -p 8888:8888 --privileged=true -v /root/www:/www centos        


docker run -p 20:20 -p 21:21 -p 88:80 -p 443:443 -p 8888:8888 -p 3306:3306 -v C:\Users\Administrator\root\www:/www --name centos_latest centos:latest 
//创建docker容器


docker ps         //查看容器


docker exec -it 容器ID /bin/bash   //进入容器      docker exec -it b811dcc30e50 /bin/bash


yum check-update -y && yum update -y && yum install initscripts screen wget -y        //升级centos并且安装必要的软件


yum install -y wget && wget -O install.sh http://download.bt.cn/install/install.sh && sh install.sh      //安装宝塔Centos安装脚本



安装成功之后退到虚拟机的centos里输入
curl ip:8888/login



保存镜像

docker commit -a "1872220587" -m "centos:centos7.6.1810 安装liunx宝塔面板免费版 5.9.1 " b811dcc30e50  centos:centos7.6.18104Bt 


docker images centos:centos7.5.1804Bt 
 



docker login    #登录到官方仓库Docker Hub



上传本地镜像centos:centos7.5.1804Bt到镜像仓库中

docker images

tag命令修改为规范的镜像
docker tag centos:centos7.6.18104Bt 1872220587/centos:centos7.6.18104Bt 


docker push 1872220587/centos:centos7.6.18104Bt 










下载镜像使用
docker pull 1872220587/centos:centos7.5.1804Bt


//创建docker容器

docker run -p 20:20 -p 21:21 -p 80:80 -p 443:443 -p 888:888 -p 8888:8888 -p 3306:3306 -v C:\Users\Administrator\root\www:/www --name Bt 1872220587/centos:centos7.5.1804Bt







进入容器

docker exec -it 29ca8f229089 /bin/bash


http://192.168.0.108:8888






使用场景：解决数据存储和修改配置文件的的问题 容器自动创建不了宿主机目录的情况

先搞一个映射目录的容器 然后把容器的文件复制到宿主机

docker run -p 20:20 -p 21:21 -p 88:80 -p 443:443 -p 8888:8888 -p 3306:3306 --name BT1 1872220587/centos:centos7.5.1804Bt


从主机复制到容器文件

docker cp C:\Users\Administrator\root\www 5f0801658154:/www



从容器复制到主机

docker cp cc6e86c70011:/www C:\Users\Administrator\root\www


docker cp f0e3b0a98d8c:/www C:\Users\Administrator\root\www



管理宝塔

进入容器
docker exec -it 38d824d99a4f /bin/bash

停止
/etc/init.d/bt stop
启动
/etc/init.d/bt start
重启
/etc/init.d/bt restart

强制修改MySQL管理(root)密码，如要改成123456
cd /www/server/panel && python tools.py root 123456


修改面板密码，如要改成12345678
cd /www/server/panel && python tools.py panel 12345678


























基本命令
仓库相关操作
docker pull     #从远程仓库拉取镜像到本地
docker push     #推送本地镜像到远程仓库
docker search   #在仓库搜索镜像
docker login    #登录到官方仓库Docker Hub
docker logout   #退出登录

镜像相关操作
docker build    #从Dockerfile构建镜像
docker pull     #同上
docker push     #同上
docker history  #显示镜像的历史信息
docker images   #列出镜像
docker rmi      #删除镜像
docker tag      #给镜像打上tag标签
docker run      #创建容器并启动容器
docker create   #创建容器
docker commit   #将修改后的容器生成镜像
docker load     #从压缩包中加载镜像
docker import   #从归档文件中创建镜像
docker save     #将镜像保存到压缩文件

容器相关操作
docker attach   #依附到一个正在运行的容器中
docker exec     #进到正在运行的容器中执行命令
docker cp       #在容器和本地系统间复制文件
docker update   #将一个容器内所有的进程从暂停状态中恢复
docker ps       #列出主机中的容器
docker port     #查找一个nat到私有网口的公共口
docker top      #查看一个容器中正在运行的进程信息
docker logs     #查看日志文件
docker diff     #检查容器内文件系统的修改
docker status   #输出容器的资源使用统计信息
docker wait     #阻塞直到容器终止
docker start    #启动已创建的容器
docker pause    #暂停运行中的容器
docker unpause  #使暂停的容器恢复运行
docker stop     #停止容器运行
docker rename   #容器改名
docker restart  #容器重启
docker kill     #关闭运行中的容器
docker rm       #删除容器
docker export   #导出容器内容为tar包
docker run      #同上
docker create   #同上
docker commit   #同上

其他基本命令
docker events   #从服务端获取实时的事件
docker info     #查看系统相关信息
docker inspect  #显示Docker对象的具体配置信息，包括容器，镜像，网络等
docker version  #输出Docker的版本信息
1
2
3
4
管理命令
docker container    #容器管理
docker image        #镜像管理
docker network      #网络管理
docker node         #节点管理
docker plugin       #插件管理
docker secret       #管理敏感数据及普通服务配置项
docker service      #服务管理
docker stack        #栈管理
docker swarm        #集群管理
docker system       #管理系统信息
docker volume       #卷管理
--------------------- 

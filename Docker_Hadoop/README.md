# 利用Docker配置Hadoop集群

[1]: https://github.com/kiwenlau/hadoop-cluster-docker	"项目地址"
[2]: https://www.bilibili.com/video/BV1M541157Mn?spm_id_from=333.337.search-card.all.click	"B站视频"

该文件夹下只有这一个README.md文件，记录相关的知识点，在后续的使用中，若发现有用得上的相关知识点都会更新进来。

## 1 安装docker

```java
curl https://get.docker.com/ | bash -s docker --mirror Aliyun
```

```
# 查看docker状态
sudo systemctl status docker
sudo systemctl start docker
```

```
# 将用户添加到docker的运行组
sudo usermod -aG docker ${whoami}
```

## 2 拉取镜像

```
sudo docker pull kiwenlau/hadoop:1.0
```

## 3 创建Hadoop网络

```
sudo docker network create --driver=bridge hadoop
```

## 4 修改start_container.sh

将端口9090和9000开放

然后运行：

```
./start-container.sh
```

## 5 启动Hadoop

```
./start-hadoop.sh 
```

## 6 搭建好后，下次开机如何启动？

```
# 启动docker
sudo systemctl start docker
```

```
# 启动各个容器
docker start xx
```

```
# 进入到hadoop-master容器（nameNode）
sudo docker exec -it hadoop-master bash
```

```
# 启动hadoop
./start-hadoop.sh 
```

## 7 将主机文件复制到docker

```
docker cp 你的文件路径 容器长ID:docker容器路径
```


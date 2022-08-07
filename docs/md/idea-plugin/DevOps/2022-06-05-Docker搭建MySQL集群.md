## Docker搭建MySQL集群

#### 单节点数据库弊病

* 大型互联网程序用户群体庞大，所以架构必须要特殊设计
* 单节点的数据库无法满足性能上的要求
* 单节点的数据库没有冗余设计，无法满足高可用

#### 常见方案：

![](../../assets/img/2022-06-05/fast_22-33-56.png)

> 重要数据建议采用PXC方案, 任一节点可读写
>
> * 同步复制，事务在所有集群节点要么同时提交，要么不提交
> * Replication采用异步复制，无法保证数据的一致性

```bash
#下载镜像
docker pull
#导入镜像
docker load
```

#### 创建内部网络

pxc 用的内部网络，外部不能直接访问

```bash
#创建内部网络，mask 子网掩码24位
docker network create --subnet=172.18.0.0/24 net1
#查看网络
docker inspect net1
#删除网络
docker network rm net1
```

#### 创建Docker卷

pxc映射数据目录

```bash
# 创建数据卷
docker volume create --name v1
#查看
docker inspect v1
#删除
docker volume v1
```

#### 创建PXC容器

```bash
docker run -d -p 3306:3306
-v v1:/var/lisb/mysql
-e MYSQL_ROOT_PASSWORD=abc123456
-e CLUSTER_NAME=PXC
#同步密码
-e XTRABACKUP_PASSWORD=abc123456
#获取真正的root权限，内部网段参数
--previleged --name==node1 --net=net1 --ip 172.18.0.2 pxc
```

其他节点同上

```bash
端口号，docker内部ip，递增，修改节点名字
增加环境变量
-e CLUSTER_JOIN=node1
```

#### 数据库的负载均衡

使用Haproxy做负载均衡，请求被均匀分发给每个节点，单节点负载低，性能好

使用Haproxy，Nginx 刚刚支持 TCP/IP ，可能存在问题， lvs 不支持Docker容器安装

![](../../assets/img/2022-06-05/fast_22-57-12.png)

**haproxy**

<img src="../../assets/img/2022-06-05/fast_22-54-36.png" style="zoom:67%;" />

```bash
docker pull haproxy
#haproxy 部分配置文件 haproxy.cfg

#数据库负载均衡
listen proxy-mysql
  #访问的IP和端口
  bind0.0.0.0:3306
  #网络协议
  mode tcp
  #负载均衡算法（轮询算法）
  #轮询算法：roundrobin
  #权重算法：static-rr
  #最少连接算法：leastconn
  #请求源IP算法：source
  balance roundrobin
  #日志格式
  option tcplog
  #在MySQL中创建一个没有权限的haproxy用户，密码为空。Haproxy
  option mysql-check user haproxy
  #check 心跳检测
  server MySQL 172.18.0.2:3306 check weight 1 maxconn 2000
  server MySQL 172.18.0.3:3306 check weight 1 maxconn 2000
  server MySQL 172.18.0.4:3306 check weight 1 maxconn 2000
  #使用keepalive检测死链
```

![](../../assets/img/2022-06-05/PotPlayerMini64_FXbEXjeN99.png)

 8888为系统管理端口



#### 双机热备，避免Haproxy故障无法代理

  关键技术： **虚拟IP地址**

![](../../assets/img/2022-06-05/Very_21-14-27.jpg)

 需要借助keepalived软件

<img src="../../assets/img/2022-06-05/fast_21-25-20.png" style="zoom:67%;" />

#### 双机热备方案 （冗余设计，高可用）

![](../../assets/img/2022-06-05/fast_21-27-58.png)

#### Docker容器 keepalived配置文件

keepalived.conf

```bash
vrrp instance VI 1{
  #身份 ，master backup，master抢占
  state MASTER 
  #网卡 映射虚拟IP
  interface eth0
  #id
  virtual router id 51
  #越高越容易抢到IP
  priority 100
  #心跳检测间隔时间 s
  advert int 1
  #心跳检测开放的账号密码
  authentication{
      auth_type 
      PASSauth_pass 123456
  }
  #可以设置多行虚拟IP
  virtual ipaddress{
  	172.18.0.201
  }
}

#启动keepalived指令
service keepalived start
#本机可以ping通
ping 172.18.0.201
```



#### 宿主机keepalived配置文件，虚拟IP映射到局域网上

宿主机上也需要安装keepalived

```bash
#定义宿主机的虚拟IP
vrrp_instance VI_1{
  state MASTER
  interface ens33
  virtual router id 51
  priority 100
  advert int 1
  authentication {
    auth type PASS
    auth pass 1111
  }
  #局域网的虚拟IP，
  virtual ipaddress {
    192.168.99.150
  }
}
#转发到Docker的虚拟IP上
#4001 是宿主机开放的端口，此处8888对应的是某个正在运行的keepaliced容器
#这个容器haproxy对应的后台管理端口是8888
virtua1 server 192.168.99.150 8888{
  #心跳检测间隔3秒
  delay loop 3
  #轮训转发
  lb_algo_rr
  #NAT模式
  lb_kind NAT
  #超时时间
  persistence timeout 50
  protocol TCP
  #从192.168.99.150 进来，转发到172.18.0.201上
  rea1_server 172.18.0.201 8888{
   weight 1
   }
}

#数据库端口
virtua1 server192.168.99.150 3306{
  delay loop 3
  lb_algo rr
  lb_kind NAT
  persistence_timeout 50
  protocol TCP
  real server  172.18.0.201  3306{
    weight 1
  }
}
```

####  暂停PXC集群的办法

```bash
#在配置文件中添加 net.ipv4.ip_forward=1 这个配置
systemctl restart network
```



#### 冷备份数据

```bash
mysql dump #冷备份
```

<img src="../../assets/img/2022-06-05/fast_22-09-14.png" style="zoom: 50%;" />

#### 热备份

<img src="..\..\assets\img\2022-06-05\fast_22-11-11.png" style="zoom: 50%;" />

#### 全量备份和增量备份

​     第一次全量备份，之后增量备份（变化的部分）

####  PXC全量恢复

* 数据库可以热备份，但是不能热还原。为了避免恢复过程中的数据同步，我们采用空白的MySQL还原数据，然后再建立PXC集群
* 还原数据前要将未提交的事物回滚，还原数据之后重启MySQL


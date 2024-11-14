---
title: Centos-DHCP
date: 2024-11-14 22:07:43
tags: [CentOS7,DHCP]
---
## 安装dhcp
> yum install -y dhcp

### 关闭防火墙，SELinux
``` bash
#关闭防火墙墙，selinux并开启dhcp服务
#临时关闭
systemctl stop firewalld
setenforce 0
#永久关闭
systemctl disable firewalld
#打开配置文件
vim /etc/selinux/config
#将SELinux修改为disabled
```
### 配置文件
>/etc/dhcp/dhcpd_config  

### 复制参考文件  

>/usr/share/doc/dhcp-4.x.x/dhcpd.conf.example  到  /etc/dhcp/dhcpd.conf 

参考配置：
``` bash
subnet <ip网段> netmask <255.255.255.0> {
  range <ip地址1>  <ip地址2>;
  option domain-name-servers <DNS服务地址>
  option domain-name <"域名">
  option routers <网关ip地址>
  option broadcast-address <以上网段的广播地址>
  default-lease-time <默认时间>(单位:秒)
  max-lease-time <最大时间>(单位:秒)
}
```

#### 绑定硬件地址
参考配置：
``` bash
host <主机名> {
  hardware ethernet <mac地址>;
  fixed-address <绑定的地址>;
}
```

#### DHCP中继
当客户端与服务器之间不直连时，在中继服务器上配置dhcp中继
>dhcrelay <dhcp服务器ip地址>

#### 查看服务状态
``` bash
#启动dhcpd服务
systemctl start dhcpd
#查看服务状态
systemctl status dhcpd
```

#### 其他
1. 当存在多个网卡时，应将主要网卡地址分配为第一个域
示例:
``` bash
#主要网卡对应的域
subnet <ip网段> netmask <255.255.255.0> {
  range <ip地址1>  <ip地址2>;
  option domain-name-servers <DNS服务地址>
  option domain-name <"域名">
  option routers <网关ip地址>
  option broadcast-address <以上网段的广播地址>
  default-lease-time <默认时间>(单位:秒)
  max-lease-time <最大时间>(单位:秒)
}
#次要网卡对应的域
subnet <ip网段> netmask <255.255.255.0> {
  range <ip地址1>  <ip地址2>;
  option domain-name-servers <DNS服务地址>
  option domain-name <"域名">
  option routers <网关ip地址>
  option broadcast-address <以上网段的广播地址>
  default-lease-time <默认时间>(单位:秒)
  max-lease-time <最大时间>(单位:秒)
}
```
如果不想为主要网卡分配域，就配置为空
``` bash
#主要网卡对应的域
subnet <ip网段> netmask <255.255.255.0> {

}
#次要网卡对应的域
subnet <ip网段> netmask <255.255.255.0> {
  range <ip地址1>  <ip地址2>;
  option domain-name-servers <DNS服务地址>
  option domain-name <"域名">
  option routers <网关ip地址>
  option broadcast-address <以上网段的广播地址>
  default-lease-time <默认时间>(单位:秒)
  max-lease-time <最大时间>(单位:秒)
}
```

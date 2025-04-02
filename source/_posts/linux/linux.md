---
title: Linux常用命令
date: 2025-04-02 21:10:06
index_img: /img/linux.png
categories:
- Linux
tags:
- 服务器部署
---

### 新增用户
  
```shell
新增用户
sudo useradd dream 

设置用户密码
sudo passwd dream

切换用户
su root

加入用户组
usermod -g root dream

增加权限
chown -R dream:root /data
```

### 切换SSH访问端口，禁止root用户登录

``` shell
vim /etc/ssh/sshd_config
```

``` shell
Port 12200 修改端口号
PermitRootLogin no 禁止root用户登录
esc :wq
systemctl restart sshd
```
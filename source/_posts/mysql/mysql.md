---
title: Linux上安装MySQL
date: 2025-04-02 21:10:06
index_img: /img/mysql.png
categories:
- Linux
tags:
- 服务器部署
- MySQL
---

### 安装MySQL
  
```shell
yum -y install mysql80-community-release-el7-7.noarch.rpm
yum -y install mysql-community-server
```

- 启动MySQL

``` shell
systemctl start mysqld.service
```

### 初始化

- 查看MySQL初始密码

```shell
grep 'password' /var/log/mysqld.log
```
- 登录MySQL

```shell
mysql -u root -p
```
- 修改MySQL密码

```shell
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
```

- 新建用户

```sql
CREATE USER 'dream'@'%' IDENTIFIED BY 'cmbjxCCWTN008#';
```
- 给新用户赋权 
- 赋予dream用户 所有数据库，所有表(* . *)  CREATE,ALTER,DELETE,INSERT,SELECT 权限 允许从任何IP登录dream用户(@'%')

```sql
GRANT CREATE,ALTER,DELETE,INSERT,SELECT ON *.* TO 'dream'@'%';
```
- 给新用户赋权
- 赋予dream用户 所有数据库，所有表，所有权限 可以用任意IP登录dream用户

```sql
GRANT ALL ON *.* TO 'dream'@'%';
```
- 刷新配置

```sql
flush privileges;
```
- 查询用户权限

```sql
select user,host from mysql.user;
```
- 修改用户访问权限 可以从任何主机(IP)登录root用户

```sql
update mysql.user set host='%' where user='root';
```
  



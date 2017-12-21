---
title: MySQL操作汇总
date: 2017-12-21 11:27:46
tags: MySQL
---

### 安装
```
Linux: sudo yum install mysql
Mac: brew install mysql
```
### 启动、停止、查看状态
```
Linux: sudo service mysqld [start|stop|status]
Mac: brew services [start|stop] mysql
```
### 生成root临时密码
```
grep 'temporary password' /var/log/mysqld.log
```
### 安全设置
```
mysql_secure_installation
```
### 查看字符集
```
show variables where variable_name like 'character%' or variable_name like 'collation%';
```
### 修改默认字符集配置
```
[client] 
default-character-set=utf8mb4 
[mysql] 
default-character-set=utf8mb4 
[mysqld] 
character-set-client-handshake=FALSE 
character-set-server=utf8mb4 
collation-server=utf8mb4_unicode_ci 
init_connect='SET NAMES utf8mb4'
```
### 修改现有数据库和表
```
alter database [db_name] character set utf8mb4 collate utf8mb4_general_ci;
alter table [table_name] convert to character set utf8mb4 collate utf8mb4_general_ci;
```
### 查看数据库和表
```
show create database [db_name];
show create table [table_name]; 
```
### 创建数据库
```
create database [db_name];
```
### 授予某用户的数据库权限
```
// 授予所有权限
1. grant all privileges on [db_name].* to [www]@'%' identified by '此处是密码';
// 授予指定权限
2. grant select, insert, delete, update on [db_name].* to [www]@'%' identified by '此处是密码';
```
### 修改用户密码
```
mysqladmin -u [user] -p password
```

### 补充
这里以"[xxx]"表示占位，可将此处替换为需要的数据库名、表明、用户名等等，替换后需要去掉"[]"
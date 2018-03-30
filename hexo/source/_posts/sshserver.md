---
title: SSH连接远程服务器的方法
date: 2018-01-20 16:35:18
tags:
categories:
---
## 方法一
```
$ ssh user@hostname [-p port] //请求登录

user@hostname's password:   //输入登录密码
```

> `user` 是目标服务器用户名
`hostname` 为我们将要登录服务器的ip地址
`port` 为端口号，不使用 `-p port`将使用，默认端口号

---
## 方法二

> 配置快捷登录方式


```
$ cd .ssh   //进入.ssh目录下
$ ls        //查看该目录下的文件
$ vi/vi config        //若 .ssh 目录下没有 config 文件，使用vi新建，弱存在使用 vi config 打开，对vim不熟悉的朋友自行查阅相关资料
```
下面配置 config文件
```
Host [name]         //名字随意取
    HostName [hostname] //支持域名
    user [root]       //root目标服务器用户名
    Port [22]         //22端口号
```
配置完成后保存文件，输入快速登录命令
```
$ ssh [name]  //请求登录

user@hostname's password:   //输入登录密码
```





---
title: Ubuntu防火墙的开启，关闭，端口的打开，查看
date: 2020-09-10 13:32:48
tags: ufw
---

+ 开启防火墙

```shell script
sudo ufw enable
```

+ 重启

```shell script
sudo ufw reload
```

+ 打开一个端口

```shell script
sudo ufw allow 8080
```

+ 查看服务器端口使用情况

```shell script
sudo ufw status
```
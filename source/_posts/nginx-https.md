---
title: nginx配置SSL证书
date: 2020-09-07 16:25:41
tags: Nginx
---

[freessl.cn](freessl.cn) 是一个提供免费HTTPS证书申请的网站

<!-- more -->

填入要申请证书的域名，全部按照默认选项即可

在 nginx 目录下 conf.d 文件夹里新建 443.conf 配置文件，文件内容如下 

<!-- more -->

```
server {
  listen 443 ssl;
  server_name breakname.com www.breakname.com;
  ssl         on;

  # path == 你自己机器上的路径,对应文件的存放位置

  root /path/breakname-com/;

  ssl_certificate /path/breakname-com/breakname.com_chain.crt; # 证书路径
  ssl_certificate_key /path/breakname-com/breakname.com_key.key; # 私钥路径

  # path == 你自己机器上的路径,对应文件的存放位置
  location /{
    root /path/build;
    index index.html index.htm;
  }
}

```
检查nginx配置文件 
```shell script
nginx -t

# nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
# nginx: configuration file /etc/nginx/nginx.conf test is successful
```
重启nginx; 
```shell script
nginx -s reload
```
去浏览器访问自己网站，如果通过https可以访问到，那就是配置成功了; /手动狗头

<font color="#dd0000">
如果你用的阿里云服务器：到安全组规则里把 443 端口添加进去
</font>





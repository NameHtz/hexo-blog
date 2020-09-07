---
title: nginx配置SSL证书
date: 2020-09-07 16:25:41
tags:
---

[freessl.cn](freessl.cn) 是一个提供免费HTTPS证书申请的网站

填入域名，全部按照默认选项即可

```
server {
  listen 443 ssl;
  server_name breakname.com www.breakname.com;
  ssl         on;

  # path == 你自己机器上的路径

  root /path/breakname-com/;

  ssl_certificate /path/breakname-com/breakname.com_chain.crt; # 证书路径
  ssl_certificate_key /path/breakname-com/breakname.com_key.key; # 私钥路径

  # path == 你自己机器上的路径
  location /{
    root /path/build;
    index index.html index.htm;
  }
}

```

<font color="#dd0000">如果你用的阿里云服务器：到安全组规则里把 443 端口添加进去</font><br />




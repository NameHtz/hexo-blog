---
title: SSL证书
date: 2020-09-07 16:25:41
tags: Nginx
---
* 前言

[freessl.cn](https://freessl.cn) 是一个提供免费HTTPS证书申请的网站；

个人网站如果购买证书，成本还是比较高的（毕竟个人网站不盈利），偶然发现可以申请免费证书，并且流程很简单，于是就找了个时间尝试搞了一下；

<!-- more -->
* 申请证书
1. 填入要申请证书的域名

2. 品牌选择：<b class="bgc-e4e6e8">亚洲诚信</b> // 双域名 有效期一年 （默认就是这个选项，到期需要手动续期）

3. 点击（创建免费的SSL证书）
4. 这一步需要选择 <b class="bgc-e4e6e8">证书类型</b>（RSA ｜ ECC）、<b class="bgc-e4e6e8">验证类型</b>（DNS ｜ 文件验证）、<b class="bgc-e4e6e8">CSR生成</b>（离线生成 ｜ 一键申请 ｜ 浏览器生成 ｜ 我有CSR），按照默认选项, 填入邮箱（点击创建）；
5. 创建之后，需要在<b class="bgc-e4e6e8">域名解析</b>按照提示添加一条记录（这一步是为了验证域名是你的）
6. 验证成功后，就可以把域名导出到 <b class="bgc-e4e6e8">KeyManager </b>；（KeyManager需要安装）
7. KeyManager --> 证书管理 --> 证书请求， <b class="bgc-e4e6e8">颁发状态</b> 是 <b class="bgc-e4e6e8">已颁发</b> 就是申请成功了；

* 导出证书

KeyManager --> 证书管理 --> 证书请求 --> 操作--更多--详情-->查看证书（右下角）--> 导出证书

* 上传到服务器

scp <本地文件名> <用户名>@<服务器IP>:<上传保存路径即文件名>

🌰
```shell script
scp /documents/file.zip root@127.0.0.1:/root 

# 把本地documents文件夹下的file.zip，用127.0.0.1的root用户上传到服务器的root目录下
```
* 配置Nginx
 
在 nginx 目录下 conf.d 文件夹里新建 443.conf 配置文件，文件内容如下 

🌰
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





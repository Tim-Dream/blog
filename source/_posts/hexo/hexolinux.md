---
title: Hexo部署到Linux上
date: 2024-11-26 14:21:16
index_img: /img/hexo.png
categories:
- Hexo
- Linux
tags:
- 服务器部署
---

### 本地编译
```
hexo generate 
hexo g
```

### 部署
- 将编译生成的`public`文件夹下的所有内容上传到Linux服务器上
- 使用NGINX代理即可
```
server {
        listen       80 default_server;
        listen       [::]:80 default_server;
        server_name  _;
        root         /opt/blog/public;
        index index.html index.htm

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        location / {
        }

        error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
    }
```

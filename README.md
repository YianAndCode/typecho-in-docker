# Typecho in Docker

## 介绍

### 环境

`php:7.4-fpm`、`nginx:latest`，该环境不包含 MySQL 数据库，但 PHP 环境已经安装 `pdo_mysql` 扩展，可以使用 MySQL 数据库

### 目录结构

```
├── app
│   └── php
│        └── Dockerfile      // PHP 镜像
├── config
│   └── nginx
│        └── typecho.conf    // nginx vhost 配置
├── logs                     // 日志目录
├── typecho                  // Typecho 源码目录
└── docker-compose.yml
```

## 用法

将 Typecho 源码放在 `typecho` 目录中（如果不存在，则新建一个，保证目录结构如上面所示即可），然后执行 `docker-composer up -d`，然后就可以在浏览器访问 `http://127.0.0.1:8001`

*因为考虑到服务器上的 80 和 443 端口可能会被 nginx 之类的程序监听，故容器中 nginx 监听的端口为 8001，如需修改，请编辑 `config/nginx/typecho.conf`*
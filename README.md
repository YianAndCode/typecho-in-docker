# Typecho in Docker

## 介绍

### 环境

`php:8.0-fpm`、`nginx:latest`，该环境不包含 MySQL 数据库，但 PHP 环境已经安装 `pdo_mysql` 和 `pdo_sqlite` 扩展，可以使用 MySQL 或者是 SQLite 数据库

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
```
cd /home
git clone https://github.com/YianAndCode/typecho-in-docker.git
cd /home/typecho-in-docker
git clone https://github.com.cnpmjs.org/typecho/typecho.git
chown -R www-data:www-data typecho/
```
这个地址`https://github.com.cnpmjs.org`为Github网站镜像站起到一个国内加速作用如果担心的话可更换`https://github.com`
将 Typecho 源码放在 `typecho` 目录中（如果不存在，则新建一个，保证目录结构如上面所示即可），然后执行 `docker-compose up -d`，然后就可以在浏览器访问 `http://127.0.0.1:8001`

*因为考虑到服务器上的 80 和 443 端口可能会被 nginx 之类的程序监听，故容器中 nginx 监听的端口为 8001，如需修改，请编辑 `docker-compose.yml`*
## 注意事项
建议克隆GitHub仓库最新的typecho仓库代码，官网打包的版本是17年的版本很久没有更新了安装时候会出现问题

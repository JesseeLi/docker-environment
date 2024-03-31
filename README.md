## docker-environment
- 这是一个自我学习的搭建 docker 环境的项目
- 目前只有 lnmp 环境

### 目录结构

- `mysql` 包含 conf、data、logs、目录，分别为 配置、持久化数据、日志等。password.txt 为数据库密码
- `nginx` 包含 conf.d、logs、目录，分别为 站点配置、日志等。
- `php`
- `redis` 包含 conf、data、logs、目录，分别为 配置、持久化数据、日志等。
- `work` 为本地项目目录

### 运行

- 执行 `docker comspose build`, 先重建 php 容器
- 执行 `docker compose up -d`
- 进入 php 容器，已经安装好 git、composer。composer 安装 laravel
- 修改 nginx 目录下 conf.d 下的配置文件
- 打开浏览器，访问 localhost:8080
- 宿主机链接 mysql
  - host:localhost
  - password:为password.txt设置的密码
  - port:3306
- 宿主机链接 redis
  - host:localhost
  - Password:123456
  - port:16379


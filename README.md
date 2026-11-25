# hello-web

用 Docker 打包的静态网页，基础镜像 nginx:stable-alpine。

## 构建镜像

```bash
docker build -t hello-web:v1 .
```

命令末尾的点表示当前目录是构建上下文，不能漏。

## 启动服务

```bash
docker run -d --name hello-web -p 127.0.0.1:8081:80 hello-web:v1
```

## 访问地址

http://127.0.0.1:8081

## 停止并移除

```bash
docker stop hello-web
docker rm hello-web
```

## 说明

- `EXPOSE 80` 只声明容器端口，不会自动发布到宿主机，必须用 `-p` 映射。
- 修改 `site/index.html` 后需要重新 `docker build` 并替换容器才能生效。
- `.dockerignore` 管构建上下文，`.gitignore` 管 Git 跟踪，两者分开维护。

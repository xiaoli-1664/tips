# 一、Docker

1. 以某个镜像启动容器，挂载本地文件夹并开启本地显示

```
docker run -it --name container_name \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e DISPLAY=unix
```
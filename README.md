# 一、Docker

1. 以某个镜像启动容器，挂载本地文件夹并开启本地显示

```
docker run -it --name container_name \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e DISPLAY=unix$DISPLAY \
-e GDK_SCALES \
-e GDK_DPI_SCALE \
-v /home/user/dataset:/dataset \
image_name /bin/bash
```

使用前在本地终端打开权限：

```
xhost +
```

2. 容器使用宿主机代理

打开配置文件：

```
vim ~/.docker/config.json
```

加入

\`
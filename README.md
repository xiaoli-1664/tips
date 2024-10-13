# Docker

## 以某个镜像启动容器，挂载本地文件夹并开启本地显示

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

## 容器使用宿主机代理

打开配置文件：

```
vim ~/.docker/config.json
```

加入

```
"proxies":
        {
          "default":
          {
            "httpProxy": "http://172.17.0.1:port",
            "httpsProxy": "http://172.17.0.1:port",
            "noProxy": "localhost, 127.0.0.1"
          }
        }
```

172.17.0.1是虚拟网关，如果容器开启时有--net host使用127.0.0.1(应该是这样，还没试过)

# Vscode

## 
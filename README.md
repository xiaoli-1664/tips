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

```plaintext
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

## cmake变量

在settings.json配置：

```
"cmake.confighreSettings":{
  "CMAKE_BUILD_TYPE": "Debug",
  "OpenCV_DIR": "/path",
}
```

## 命令行参数

settings.json配置：

```
"cmake.debugConfig": {
  "args": [
  "arg1", "arg2",
]
}
```

# Ubunntu

## 删除之前添加的源

```
sudo rm /etc/apt/sources.list.d/xxx.list
```

## 关联git帐号，配置ssh

1. 配置git帐号

```
git config --global user.name "name"
git config --global user.email "email"
```

2. 生成ssh key

```
ssh-keygen -t rsa -C "email"
```

3. 复制输出密钥

```plaintext
cat /home/xxx/.ssh/id_rsa.pub
```

4. 登陆github帐号，添加公钥

```plaintext
setting --> SSH and GPGS Keys --> New  SSH Key-->复制cat id_rsa.pub里的秘钥到指定位置-->Add SSH Key
```

# Vim

1. 取消显示virtual_text（诊断信息）

```
lua vim.diagnostic.config({virtual_text=false})
```
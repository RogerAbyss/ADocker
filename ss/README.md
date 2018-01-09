# Shadowsocks

 - [x] 科学上网

## Install

- 拉取镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/abyss/shadowsocks
```

- 运行容器
```
docker run -dt --name ss \
 -p 1723:1723 \
 -p 1724:1724/udp \
 registry.cn-hangzhou.aliyuncs.com/abyss/shadowsocks \
 -s "-s :: -s 0.0.0.0 -p 1723 -m aes-256-cfb -k dockone.io --fast-open" \
 -k "-t 127.0.0.1:1724 \
 -l :1724 -mode fast2" -x
```


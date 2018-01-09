# Pure-FTP

 - [x] FTP服务器

## Install

- 拉取镜像
```
sudo docker pull registry.cn-hangzhou.aliyuncs.com/abyss/pure-ftpd
```

- 运行docker
```
docker run -dt --name ftpd_server \
-p 21:21 \
-p 60001-60101:60001-60101 \
-e "PUBLICHOST=localhost" --privileged=true \
-v /home/ftpusers/abyss:/home/ftpusers/abyss \
registry.cn-hangzhou.aliyuncs.com/abyss/pure-ftpd bash
```

- 进入docker
```
docker exec -it ftpd_server /bin/bash
```

- 添加用户
```
pure-pw useradd abyss -u ftpuser -d /home/ftpusers/abyss
pure-pw mkdb
```

- 重新启动
```
# 人数根据之前的端口号相关
/usr/sbin/pure-ftpd -c 50 -C 50 \
-l puredb:/etc/pure-ftpd/pureftpd.pdb \
-E -j -R \
-P $PUBLICHOST \
-p 60001:60101 &

# 目录权限正确才能访问
chmod -R 777 /home/ftpusers/abyss
```


FROM influxdb:1.2

LABEL maintainer="roger_ren@qq.com"

USER root

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone

RUN date -R
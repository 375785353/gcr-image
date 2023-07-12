FROM ubuntu:focal
  
ARG GID=10000
ARG GROUP=nym
ARG UID=10000
ARG USER=nym
ARG NYM_VERSION=v0.32.0
ARG NYM_REPOSITORY_URL=https://github.com/nymtech/nyxd/releases/download/${NYM_VERSION}/nyxd-ubuntu-20.04.tar.gz


RUN  sed -i 's/archive\.ubuntu\.com/mirrors.aliyun.com/g' /etc/apt/sources.list && \
     sed -i 's/security\.ubuntu\.com/mirrors.aliyun.com/g' /etc/apt/sources.list && \
     apt update && apt upgrade -y && apt install -y software-properties-common && \
     apt install -y curl git wget && \
     wget ${NYM_REPOSITORY_URL} && tar xf nyxd-ubuntu-20.04.tar.gz && \
     mv libwasmvm.x86_64.so /lib/x86_64-linux-gnu/ && mv nyxd /usr/bin/nyxd && \
     chmod 755 /usr/bin/nyxd && \
     apt remove -y software-properties-common make git && \
     rm -rf /var/lib/apt

EXPOSE 1317/tcp 26656/tcp 26660/tcp 80/tcp

ENTRYPOINT ["bash"]


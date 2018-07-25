FROM ubuntu

# MAINTAINER
MAINTAINER json_hc@163.com
RUN apt-get update
RUN apt-get install -y wget
RUN apt-get install -y gcc automake autoconf libtool make
RUN apt-get install -y build-essential
RUN apt-get install -y libncurses5-dev
RUN wget http://www.lua.org/ftp/lua-5.1.5.tar.gz
RUN tar -zxvf  lua-5.1.5.tar.gz
WORKDIR lua-5.1.5
RUN apt-get install -y libreadline-dev
RUN make linux && make install

WORKDIR  /
RUN wget https://github.com/coreos/etcd/releases/download/v3.2.6/etcd-v3.2.6-linux-amd64.tar.gz
RUN tar -zxvf etcd-v3.2.6-linux-amd64.tar.gz -C /opt/
RUN rm -rf etcd-v3.2.6-linux-amd64.tar.gz
WORKDIR /opt
RUN mv etcd-v3.2.6-linux-amd64  etcd-v3.2.6
RUN mkdir /etc/etcd


ENV TZ=Asia/Shanghai

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update
RUN apt-get install tzdata

RUN dpkg-reconfigure --frontend noninteractive tzdata

RUN apt-get install -y software-properties-common
RUN apt-add-repository ppa:ondrej/php
RUN  apt-get update

RUN apt-get install -y  php7.1
RUN apt-get install -y php7.1-mysql php7.1-gd php7.1-curl php7.1-memcache


RUN wget -c http://luajit.org/download/LuaJIT-2.0.2.tar.gz
RUN tar zxvf LuaJIT-2.0.2.tar.gz
RUN rm -rf LuaJIT-2.0.2.tar.gz
WORKDIR  ./LuaJIT-2.0.2
RUN make install PREFIX=/usr/local/luajit
RUN  echo "/usr/local/luajit/lib" > /etc/ld.so.conf.d/usr_local_luajit_lib.conf
RUN ldconfig
RUN export LUAJIT_LIB=/usr/local/luajit/lib
RUN export LUAJIT_INC=/usr/local/luajit/include/luajit-2.0

RUN apt-get install -y net-tools
RUN apt-get install -y vim

RUN apt-get install -y  mysql-client
RUN apt-get install -y libmysqlclient-dev


RUN mkdir /data
COPY  data_game.tar.gz /data/
WORKDIR  /data
RUN tar -zxvf data_game.tar.gz ./
RUN rm -rf data_game.tar.gz

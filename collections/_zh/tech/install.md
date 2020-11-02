---
title: radard的安装
chapter: 3
order: 2
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# radard的安装

## 0. 准备

* OS推荐：Ubuntu 14.04 64bit，以下都以此系统为例
  * 物理需求（至少）：
    * CPU：8Core
    * RAM：64G
    * 硬盘：
      * 默认配置文件中把数据存储配置在/var/db/radard目录下，需要至少500G SSD，建议和系统盘分开
      * 日志文件默认配置存储在/var/log目录下，建议至少50G，和系统盘分开
      * 如果需要保存和查询历史交易，需要配置成带历史交易数据库节点（通过sqlite或本地mysql服务）
        * sqlite默认配置存储在/var/db/radard/目录下，需要额外至少500G SSD
        * MySQL需要单独安装服务，建议额外至少500G硬盘

### 必备软件

  * 基础库
    
  ```
  sudo apt-get update
  sudo apt-get install libssl-dev libboost1.55-all-dev -y
  ```
    
  * install google protobuf
  
  ```
  sudo apt-get install protobuf-compiler libprotobuf-dev -y
  ```

  * 编译软件
  
  ```
  sudo apt-get install pkg-config scons git g++ -y
  ```

  * 使用MySQL存历史交易需要额外安装MySQL开发库
  
  ```
  sudo apt-get install libmysqlclient-dev -y
  ```

### 相关配置
  
  * 取消swap
  
  ```
  #radard比较消耗内存，内存不足建议直接让系统杀掉它，让它重启，而不是消耗swap导致系统不稳定，命令为
  sudo /sbin/swapoff -a
  #注释掉/etc/fstab里的swap分区那一行确保重启后也不使用swap
  free  #free命令查看swap是否全为0
  ```

  * 同步系统时间
  
  ```
  sudo /usr/sbin/ntpdate pool.ntp.org 
  #TODO：添加到crontab里，定期同步时间
  ```

## 1. 编译
  
  * clone最新的radard代码
  
  ```
  cd /opt/
  sudo git clone https://github.com/radrbiz/radard
  ```

  * 使用scons手动编译

  ```
  cd /opt/radard/
  sudo scons
  ```

  * 如果需要使用MySQL，请使用 ''sudo scons -Q use-mysql=1'' 编译

## 2. 创建账号

  ```
  #创建账号
  sudo useradd radard -u 10001 -m
  ```

## 3. 配置

配置文件复制到/etc/radar/下

  ```
  sudo mkdir /etc/radar
  sudo cp doc/radar-example.cfg /etc/radar/radard.cfg
  ```

修改配置文件使用命令 ''sudo vi /etc/radar/radard.cfg'' ，部分常用的配置有：

  * 启用MySQL存储历史交易
    * 如需使用MySQL存储历史交易，请先在mysql中创建一个独立数据库和用户，并将此数据库授权给新建的用户，然后将transaction_db配置如下，其中host是mysql服务所在主机，port是端口，database是数据库名，username是有权访问此数据库的用户，password对应密码

    ```
    [transaction_db]
    type=mysql
    host=127.0.0.1
    port=3306
    database=transaction
    username=mysql_user
    password=mysql_pass
    ```

  * 禁用历史交易存储
    * 默认历史交易存储使用sqlite本地存储，这样会额外消耗磁盘和性能，如果不需要查询历史交易可直接禁用此存储，配置中增加以下信息
    
    ```
    [transaction_db]
    type=none
    ```

  * 启用temp_db加速读写
    * temp_db可以利用更高速的硬盘来作为临时缓存，例如/media/ephemeral0是一个更高速的硬盘，配置文件增加如下内容（注意手工创建目录 ''mkdir -p /media/ephemeral0/radar/rocksdb'' 并 ''chown radard.radard /media/ephemeral0/radar/rocksdb ''）
    
    ```
    [temp_db]
    type=RocksDB
    path=/media/ephemeral0/radar/rocksdb
    open_files=2000
    filter_bits=12
    cache_mb=256
    file_size_mb=8
    file_size_mult=2
    ```

## 4. 运行 

  * 安装可执行程序
  
    ```
    sudo cp build/radard /usr/local/sbin/
    ```

  * 创建启动脚本
  
    ```
    sudo ln -fs /opt/radard/doc/radard.init /etc/init.d/radard
    ```

  * 启动
  
    ```
    sudo service radard start
    ```

  * 开机自启动
    
    ```
    sudo update-rc.d radard defaults
    sudo update-rc.d radard enable
    ```

# radard常用命令

  * 启动：service radard start
  * 停止：service radard stop
  * 重启：service radard restart
  * 强行停止： killall /usr/local/sbin/radard
  * 查看radar信息： service radard status
  * 执行radard命令，如peers： service radard command peers

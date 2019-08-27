### 下载elastic search 7.3.1
```
 wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.1-linux-x86_64.tar.gz
```
### 解压
```
 tar -zxvf elasticsearch-7.3.1-linux-x86_64.tar.gz
```
### 下载JDK 11
```
wget https://download.java.net/java/GA/jdk11/13/GPL/openjdk-11.0.1_linux-x64_bin.tar.gz
```
### 解压
```
 tar -zxvf elasticsearch-7.3.1-linux-x86_64.tar.gz openjdk-11.0.1_linux-x64_bin.tar.gz
```
### 修改 bin/elasticsearch,指定jdk版本
vi bin/elasticsearch
```
# 配置自己的jdk11
export JAVA_HOME=/opt/jdk-11.0.1
export PATH=$JAVA_HOME/bin:$PATH


# 添加jdk判断
if [ -x "$JAVA_HOME/bin/java" ]; then
        JAVA="/opt/jdk-11.0.1/bin/java"
else
        JAVA=`which java`
fi
```
### 修改jvm.options
vi conf/jvm.options
```
## -XX:+UseConcMarkSweepGC
-XX:+UseG1GC
```
### 创建elsearch用户组及elsearch用户
```
groupadd elsearch
useradd elsearch -g elsearch -p elasticsearch
```
### 更改elasticsearch文件夹及内部文件的所属用户及组为elsearch:elsearch
```
chown -R elsearch:elsearch  elasticsearch
```
### 解决启动报错 1 
[1]: max file descriptors [4096] for elasticsearch process is too low, increase to at least [65535]
[2]: max number of threads [3800] for user [esuser] is too low, increase to at least [4096]
```
# 切换root用户
[root@localhost config]# vi /etc/security/limits.conf
# 添加如下4行内容
*        soft    nofile      65536
*        hard    nofile      65536
*        soft    nproc       4096
*        hard    nproc       4096
```
### 解决启动报错 2
[3]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
```
[root@localhost config]# vi /etc/sysctl.conf
# 添加下面这行
vm.max_map_count=655360
```

### 切换到elsearch用户再启动
```
su elsearch # 切换账户
加载设置好的系统参数
sysctl [-n] [-e] -p <filename> (default /etc/sysctl.conf)
sudo sysctl -p
cd elasticsearch/bin # 进入你的elasticsearch目录下的bin目录
./elasticsearch
```

### 访问elasticsearch
```
 xxx.xxx.xxx.xxx:9200
```



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
### 切换到elsearch用户再启动
```
su elsearch # 切换账户
cd elasticsearch/bin # 进入你的elasticsearch目录下的bin目录
./elasticsearch
```



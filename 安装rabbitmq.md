### 安装erlang
```
sudo yum install gcc glibc-devel make ncurses-devel openssl-devel autoconf
tar zxvf otp_src_R15B01.tar.gz
wget http://erlang.org/download/otp_src_22.0.tar.gz
cd otp_src_22.0.tar.gz
./configure && make && sudo make install
```
### 0依赖erlang安装

>https://github.com/rabbitmq/erlang-rpm/releases

>https://github.com/rabbitmq/rabbitmq-server/releases`

```
cd /usr/local
wget https://github.com/rabbitmq/erlang-rpm/releases/download/v22.0.7/erlang-22.0.7-1.el7.x86_64.rpm
yum -y install erlang-22.0.7-1.el7.x86_64.rpm
wget https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.7.16/rabbitmq-server-3.7.16-1.el7.noarch.rpm
yum -y install rabbitmq-server-3.7.16-1.el7.noarch.rpm

```
### 查找默认配置
`find / -name rabbitmq-defaults`

### 启动rabbitmq
`nohup ./rabbitmq-server start &`

### 启动可视化界面
`./rabbitmq-plugins enable rabbitmq_management`

### 查看日志
`tail -f  /var/log/rabbitmq/rabbit\@iZj6cdtcbwezle8l9i1e7zZ.log`

---

### 常用操作
#### rabbitmqctl



>官方文档 https://www.rabbitmq.com/rabbitmqctl.8.html
```
添加用户
./rabbitmqctl add_user username password

设置超级管理员权限
./rabbitmqctl set_user_tags username administrator

用户列表
./rabbitmqctl list_users

删除用户
./rabbitmqctl rabbitmqctl delete_user username

修改密码
./rabbitmqctl change_password username newpassword

列出虚拟主机
./rabbitmqctl list_vhosts

设置用户权限
-p(必填) vhost(虚拟机名称) user(用户名) conf(配置权限正则) write(写入权限正则) read(读取权限正则)
./rabbitmqctl set_permissions -p [my-vhost] / username ".*" ".*" ".*"

列表所有权限
./rabbitmqctl list_permissions -p my-vhost

列出指定用户权限
./rabbitmqctl list_user_permissions username
```



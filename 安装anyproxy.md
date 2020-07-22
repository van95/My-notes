### 安装anyproxy

1. 安装node
```
yum install nodejs
```
2. 安装anyproxy
```
npm install -g anyproxy
```
3. 安装ca证书
```
anyproxy--ca
```
4. 启动anyproxy
```
nohup anyproxy --intercept  > anyproxy_log.log &
```
5. 访问 ip:8002,下载证书,安装证书,ios系统在 设置->通用->关于本机->证书信任设置->启用信任开关
6. 打开当前连接的wifi->最下面配置代理->设置手动->服务器填写服务器ip,端口8001

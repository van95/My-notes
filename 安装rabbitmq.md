### 安装erlang
```
 - sudo yum install gcc glibc-devel make ncurses-devel openssl-devel autoconf
 - tar zxvf otp_src_R15B01.tar.gz
 - wget http://erlang.org/download/otp_src_22.0.tar.gz
 - cd otp_src_22.0.tar.gz
 - ./configure && make && sudo make install
```
### 卸载erlang
 ```
    19.x版本后默认安装位置在/usr/local/lib/erlang/

    rm -rf /usr/local/lib/erlang/
 ```


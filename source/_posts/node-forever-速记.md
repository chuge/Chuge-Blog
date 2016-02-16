title: node forever 速记
date: 2016-02-16 18:30:06
tags:
---

### Run server

``` bash
$ sudo npm install forever -g   #安装
$ sudo forever start ./bin/www          #启动
$ sudo forever stop 0           #关闭
$ sudo forever list #查看
$ sudo forever start -l forever.log -o out.log -e err.log app.js   #输出日志和错误
```
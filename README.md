# Licode

An Open Source WebRTC Communications Platform.

With Licode you can host your own WebRTC conference provider and build applications on top of it with easy to use APIs: [client-side](http://licode.readthedocs.io/en/master/client_api/) and [server-side](http://licode.readthedocs.io/en/master/server_api/).

You have two options to start using Licode:

* If you want a quick taste of what Licode can do or you are familiar with [Docker](http://www.docker.com) - [How to use the docker image or build your own](http://licode.readthedocs.io/en/master/docker/)

* If you are interested in contributing, want to get a better view of the Licode architecture or you don't trust those fancy containers - [How to build Licode from source](http://licode.readthedocs.io/en/master/from_source/)

## Community Forums

Most discussions take place in the [Licode discourse](http://discourse.lynckia.com/). Please feel free to jump in to discuss anything Licode or WebRTC related. This is also a good place to find answers for your Licode problems.

## Contributing

You can find our contributing guide [here](http://lynckia.com/licode/contribute.html).

## Code Of Conduct

This project adheres to the Contributor Covenant code of conduct. By participating, you are expected to uphold this [code](https://github.com/lynckia/licode/blob/master/CODE_OF_CONDUCT.md).

## License

[MIT License](https://github.com/lynckia/licode/blob/master/LICENSE).

More info at:
http://www.lynckia.com/licode



## v8 tag uses supervisor for process management

**安装supervisor**

```shell
$ apt-get install supervisor
# 启动
$ supervisord -c /etc/supervisord.conf
```

**为node建立软连接**

```shell
$ ln -s /opt/licode/build/libdeps/nvm/versions/node/v12.13.0/bin/node /usr/bin/node
```

**配置.conf文件**

```shell
$ cd /etc/supervisor/conf.d 
$ vim licode.conf
# 输入如下配置
[program:nove]
directory=/opt/licode/nuve/nuveAPI/
command=node nuve.js
stdout_logfile=/opt/log/licode/nove.log
autostart=true
autorestart=true
startsecs=8
stopasgroup=true
ikillasgroup=true
startretries=1
redirect_stderr=true

[program:erizo_controller]
directory=/opt/licode/erizo_controller/erizoController/
command=node erizoController.js
stdout_logfile=/opt/log/licode/erizo_controller.log
autostart=true
autorestart=true
startsecs=8
stopasgroup=true
ikillasgroup=true
startretries=1
redirect_stderr=true

[program:erizo_agent]
directory=/opt/licode/erizo_controller/erizoAgent/
command=node erizoAgent.js
stdout_logfile=/opt/log/licode/erizo_agent.log
autostart=true
autorestart=true
startsecs=8
stopasgroup=true
ikillasgroup=true
startretries=1
redirect_stderr=true

[program:basic_example]
directory=/opt/licode/extras/basic_example/
command=node basicServer.js
stdout_logfile=/opt/log/licode/basic_example.log
autostart=true
autorestart=true
startsecs=8
stopasgroup=true
ikillasgroup=true
startretries=1
redirect_stderr=true
```

**supervisor 命令使用**

```shell
$ supervisorctl status        //查看所有进程的状态
$ supervisorctl stop es       //停止es
$ supervisorctl start es      //启动es
$ supervisorctl restart       //重启es
$ supervisorctl update        //配置文件修改后使用该命令加载新的配置
$ supervisorctl reload        //重新启动配置中的所有程序
$ supervisorctl reread        //重新启动配置中的所有程序
```

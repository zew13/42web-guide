# SSH Tunnel

### 采用 SSH Tunnel 反向连接到内网服务器
```
系统方案： 内网有一台服务, 外网有一台服务器。通过外网一台服务器做跳板。连接到内网服务器。比如让外网服务器访问内网服务器的80端口并登陆22.

A： 内网: 一台docker虚拟机
B： 外网：196.114.23.12

```
这里我们需要实现反向隧道：修改`/etc/ssh/sshd_config`中的   ` GatewayPorts  yes `, 然后重启` /etc/init.d/sshd restart`。


    $ autossh -M 5678 -N -R 6000:localhost:22 user1@196.114.23.12

-M 5678参数，负责通过5678端口监视连接状态，连接有问题时就会  自动重连。
其中6000 指 远程服务器上面的端口, 22是内网服务上面的端口。

当尝试连接成功后，并在外网服务器上面尝试:

    $ ssh localhost -p 6000

尝试是否设置成功。

如何设置代理访问内网web 服务：这里会采用nginx反向代理。

首先在内网服务器安装好nginx服务。

内网服务器配置方法：

    $ autossh -M 5656 -N -R 4000:localhost:80 user1@196.114.23.12

外网服务器配置nginx 反向代理：

```
server{
    listen       80;
    server_name   aa.abc.com;

    location / {
        proxy_pass http://127.0.0.1:4000;
        proxy_set_header Host $host:80;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Via "nginx";
    }
}

```

重启 nginx服务。

尝试访问外网IP测试是否配置成功。


### Tips

如何测试配置成功在远程服务器上：

    $ netstat -pan | grep 4000

尝试查看后台端口是否监听。

# docker

docker run -t -i -p 80:80 --name 42web e08757e1bc77 /bin/bash
docker start -i b012910914d1
docker ps -a

docker rm $(docker ps -q -a)
一次性删除所有的容器

docker rmi $(docker images -q)
一次性删除所有的镜像。

docer export 对应导入的命令是cat xxx | docker import - name 。我这里用的是niubi：latest ......

$ sudo ifconfig docker0
docker0 Link encap:Ethernet HWaddr xx:xx:xx:xx:xx:xx
inet addr:172.17.42.1 Bcast:0.0.0.0 Mask:255.255.0.0

http://linuxwiki.github.io/Services/Docker.html#62docker0-ip

docker export bb6ce0f8e59c |bzip2 -c > 42.tar.bz2

sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 172.17.0.17:80


mysql 密码 42web
解析

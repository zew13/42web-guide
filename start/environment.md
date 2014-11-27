Docker Development Environment Guide
====================================

### Requirement:

Mac OS:
* [Homebrew link](http://brew.sh/)
* [Docker link](http://www.docker.com)
* Dnsmasq

### 如何安装:

#### Homebrew:

Install Homebrew, 在Terminal中运行:

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

#### Docker:

下载最新的docker:
[Github Download link](https://github.com/boot2docker/osx-installer/releases/)

英文官方文档参考:
[Official English Edition](https://docs.docker.com/installation/mac/)

中文翻译版本:
[中文](http://www.widuu.com/chinese_docker)

### Dnsmasq

    brew install dnsmasq

设置开机启动

    sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist

配置 Dnsmasq

    cp /usr/local/opt/dnsmasq/dnsmasq.conf.example /usr/local/etc/dnsmasq.conf


参考 2.4.5 docker

TODO add come configuration

















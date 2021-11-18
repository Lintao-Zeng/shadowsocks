shadowsocks
===========

[![PyPI version]][PyPI]
[![Build Status]][Travis CI]

A fast tunnel proxy that helps you bypass firewalls.

Features:
- TCP & UDP support
- User management API
- TCP Fast Open
- Workers and graceful restart
- Destination IP blacklist

Server
------

### ss.config
```
{
    "server":"0.0.0.0",
    "server_port":8388,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"123456",
    "timeout":600,
    "method":"cr4-md5",
    "fast_open":true
}
```
```
git clone -b master https://github.com/shadowsocks/shadowsocks
```

### Recommend Python3.7.3
```
pip install ./shadowsocks
```
### Start Server
```
ssserver -c ss.json -d start
```
-c 加载配置

-d 后台运行

目前支持的比较快的加密方法有rc4和rc4-md5，但是rc4服务端会提示不安全，并且很多客户端也不支持，所以rc4-md5比较合适。

设置成none的话，服务端会提示不支持的加密方法，所以说官方并没有为ss设置不加密选项。

fast_open需要服务端和客户端的linux内核都大于3.7+才有效，不过开着也没什么影响。

### SS各加密方式参考速度
```
aes-128-cfb 0.368462085724s
aes-128-ofb 0.400309085846s
aes-192-cfb 0.452577829361s
aes-192-ofb 0.381041049957s
aes-256-cfb 0.418514966965s
aes-256-ofb 0.405379056931s
cast5-cfb 0.859935045242s
cast5-ofb 0.911785125732s
chacha20 0.429271936417s
rc4 0.154517173767s
rc4-md5 0.169504165649s
salsa20 0.44139790535s
```

### Install

Debian / Ubuntu:

    apt-get install python-pip
    pip install git+https://github.com/shadowsocks/shadowsocks.git@master

CentOS:

    yum install python-setuptools && easy_install pip
    pip install git+https://github.com/shadowsocks/shadowsocks.git@master

For CentOS 7, if you need AEAD ciphers, you need install libsodium
```
dnf install libsodium python34-pip
pip3 install  git+https://github.com/shadowsocks/shadowsocks.git@master
```
Linux distributions with [snap](http://snapcraft.io/):

    snap install shadowsocks

Windows:

See [Install Shadowsocks Server on Windows](https://github.com/shadowsocks/shadowsocks/wiki/Install-Shadowsocks-Server-on-Windows).

### Usage

    ssserver -p 443 -k password -m aes-256-cfb

To run in the background:

    sudo ssserver -p 443 -k password -m aes-256-cfb --user nobody -d start

To stop:

    sudo ssserver -d stop

To check the log:

    sudo less /var/log/shadowsocks.log

Check all the options via `-h`. You can also use a [Configuration] file
instead.

If you installed the [snap](http://snapcraft.io/) package, you have to prefix the commands with `shadowsocks.`,
like this:

    shadowsocks.ssserver -p 443 -k password -m aes-256-cfb
    
### Usage with Config File

[Create configuration file and run](https://github.com/shadowsocks/shadowsocks/wiki/Configuration-via-Config-File)

To start:

    ssserver -c /etc/shadowsocks.json


Documentation
-------------

You can find all the documentation in the [Wiki](https://github.com/shadowsocks/shadowsocks/wiki).

License
-------

Apache License







[Build Status]:      https://img.shields.io/travis/shadowsocks/shadowsocks/master.svg?style=flat
[PyPI]:              https://pypi.python.org/pypi/shadowsocks
[PyPI version]:      https://img.shields.io/pypi/v/shadowsocks.svg?style=flat
[Travis CI]:         https://travis-ci.org/shadowsocks/shadowsocks


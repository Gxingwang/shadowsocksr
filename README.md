ShadowsocksR
===========

[![Build Status]][Travis CI]

A fast tunnel proxy that helps you bypass firewalls.

Server
------

### Install

Debian / Ubuntu:

    apt-get install git
    git clone https://github.com/shadowsocksr/shadowsocksr.git

CentOS:

    yum install git
    git clone https://github.com/shadowsocksr/shadowsocksr.git

Windows:

    git clone https://github.com/shadowsocksr/shadowsocksr.git

### Usage for single user on linux platform

If you clone it into "~/shadowsocksr"  
move to "~/shadowsocksr", then run:

    bash initcfg.sh

move to "~/shadowsocksr/shadowsocks", then run:

    python server.py -p 443 -k password -m aes-128-cfb -O auth_aes128_md5 -o tls1.2_ticket_auth_compatible

Check all the options via `-h`.

You can also use a configuration file instead (recommend), move to "~/shadowsocksr" and edit the file "user-config.json", then move to "~/shadowsocksr/shadowsocks" again, just run:

    python server.py

To run in the background:

    ./logrun.sh

To stop:

    ./stop.sh

To monitor the log:

    ./tail.sh

### Docker
------
    docker run -d --name=ssr -p 24799:8388 -e PASSWORD='sunday' -e METHOD='chacha20-ietf' -e PROTOCOL='auth_aes128_md5' sundayle/shadowsocksr:manyuser
------    
    SERVER_ADDR     0.0.0.0
    SERVER_PORT     8388
    PASSWORD        sunday
    METHOD          chacha20-ietf
    PROTOCOL        auth_aes128_md5
    OBFS            tls1.2_ticket_auth
    
docker-compose
------

    cat docker-compose.yml
    shadowsocksr:
      image: breakwa11/shadowsocksr
      ports:
        - "8388:8388/tcp"
        - "8388:8388/udp"
      environment:
        - METHOD=aes-256-gcm
        - PASSWORD=9MLSpPmNt
      restart: always   
-----

    curl -L https://github.com/docker/compose/releases/download/1.23.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose
    cp docker-compose.yml .
    docker-compose up -d




Client
------

* [Windows] / [macOS]
* [Android] / [iOS]
* [OpenWRT]

Use GUI clients on your local PC/phones. Check the README of your client
for more information.

Documentation
-------------

You can find all the documentation in the [Wiki].

License
-------

Copyright 2015 clowwindy

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
License for the specific language governing permissions and limitations
under the License.

Bugs and Issues
----------------

* [Issue Tracker]



[Android]:           https://github.com/shadowsocksr/shadowsocksr-android
[Build Status]:      https://travis-ci.org/shadowsocksr/shadowsocksr.svg?branch=manyuser
[Debian sid]:        https://packages.debian.org/unstable/python/shadowsocks
[iOS]:               https://github.com/shadowsocks/shadowsocks-iOS/wiki/Help
[Issue Tracker]:     https://github.com/shadowsocksr/shadowsocksr/issues?state=open
[OpenWRT]:           https://github.com/shadowsocks/openwrt-shadowsocks
[macOS]:             https://github.com/shadowsocksr/ShadowsocksX-NG
[Travis CI]:         https://travis-ci.org/shadowsocksr/shadowsocksr
[Windows]:           https://github.com/shadowsocksr/shadowsocksr-csharp
[Wiki]:              https://github.com/breakwa11/shadowsocks-rss/wiki

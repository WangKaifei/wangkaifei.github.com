---
layout: post
title: CentOS-7 Bootstrap
---
调整时区为东八区

    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

安装常用网络工具

    yum install epel-release -y 
    yum update -y 
    yum install bind-utils screen htop nload mtr traceroute iftop tree supervisor whois -y
    wget -P /usr/local/bin/ https://www.neiwang.pub/downloads/besttrace && chmod 744 /usr/local/bin/besttrace
    wget -P /usr/local/bin/ https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py && chmod 744 /usr/local/bin/speedtest.py
    wget -P /usr/local/bin/ https://raw.githubusercontent.com/oooldking/script/master/superspeed.sh && chmod 744 /usr/local/bin/superspeed.sh
    wget -P /usr/local/bin/ https://raw.githubusercontent.com/oooldking/script/master/superbench.sh && chmod 744 /usr/local/bin/superbench.sh
    wget -P /usr/local/bin/ https://raw.githubusercontent.com/teddysun/across/master/bench.sh && chmod 744 /usr/local/bin/bench.sh

supervisor 管理命令

    systemctl enable supervisord
    systemctl start supervisord
    supervisorctl reload

更换内核，开启 bbr

    rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
    rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
    yum --enablerepo=elrepo-kernel install kernel-ml -y
    echo "net.core.default_qdisc = fq
    net.ipv4.tcp_congestion_control = bbr" >> /etc/sysctl.conf
    grub2-set-default 0
    reboot

删除不必要的内核

    yum remove kernel kernel-ml -y
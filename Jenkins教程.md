1、Jenkins安装
国内由于qiang的存在，网上提供的yum或者apt-get方式都不行。
所以建议采用离线安装的方式，即采用war包或者deb安装方式。

为了后续安装插件方便，强烈建议使用war安装。
具体操作如下：
1、国内清华源

切记使用国内插件json文件。直接使用清华源更新插件，本质还是使用国外源。下载速度很慢。

2、建议先将jenkins汉化

GitLab

https://www.cnblogs.com/bycnboy/p/10594198.html

GitLab安装步骤
1、基础文件

    yum install -y curl 
    yum install -y policycoreutils-python
    yum install -y openssh-server
    yum install -y openssh-clients
    yum install -y postfix
    yum install -y cronie
    yum install -y lokkit
    
    systemctl enable sshd
    systemctl start
    systemctl enable postfix
    systemctl start postfix
    chkconfig postfix on
    lokkit -s http -s ssh


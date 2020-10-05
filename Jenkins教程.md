1、Jenkins安装
国内由于qiang的存在，网上提供的yum或者apt-get方式都不行。
所以建议采用离线安装的方式，即采用war包或者deb安装方式。

为了后续安装插件方便，强烈建议使用war安装。
具体操作如下：
1、国内清华源

切记使用国内插件json文件。直接使用清华源更新插件，本质还是使用国外源。下载速度很慢。

2、建议先将jenkins汉化
汉化插件之间从Jenkins中文社区下载。

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

2、安装GitLab
直接配置清华源，yum安装就行了，版本自己制定，建议10.0以上版本

    sudo yum install gitlab-ce

2、基础配置

配置external_url

    vi /etc/gitlab/gitlab.rb
    external_url '你的IP'

修改服务端口

    vi /etc/gitlab/gitlab.rb
    unicorn['port']=你想的端口号

修改之后切记重新配置

    sudo gitlab-ctl reconfigure

状态、停止、启动、重启

    sudo gitlab-ctl status
    sudo gitlab-ctl stop
    sudo gitlab-ctl start
    sudo gitlab-ctl restart

查看日志

    sudo gitlab-ctl tail

Gerrit安装

建议用war包安装，和Jenkins一样的。这样子比较好操作。

端口需要修改为8083

Gerrit的插件配置后续单独整理

    sudo rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
    sudo yum install -y nginx
    cat default.conf_bak 
    cp -r default.conf_bak gerrit.conf
    vi gerrit.conf 
    rm -rf gerrit.conf 
    vi gerrit.conf
    sudo chmod 755 /home/gerrit 
    htpasswd
    yum -y install httpd-tools
    htpasswd -c /home/gerrit/gerrit.password admin 
    htpasswd -m /home/gerrit/gerrit.password zycgerrit
    sudo service nginx restart 
    vi gerrit.conf 
    systemctl status nginx.service
    cd /etc/nginx/
    ls
    cat nginx.conf 
    systemctl status nginx.service
    getenforce　　　　
    setenforce 0 
    systemctl status nginx.service
    sudo service nginx restart 
    cd /home/gerrit/
    ls
    cd gerrit_site/
    ls
    cd bin/
    ls
    ./gerrit.sh restart 
    ifconfig
    cd /etc/nginx/
    cd conf.d/
    ls
    vi gerrit.conf 
    sudo service nginx restart 
    cd /home/gerrit/gerrit_site/bin/
    ./gerrit.sh restart 
    cd /etc/apache2
    cd /etc/apache
    cd /etc
    cd /home/gerrit/gerrit_site/etc
    ls
    vi gerrit.config 
    history

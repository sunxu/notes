# first step after installing Debian

---

* 更新软件源

编辑apt-get的源列表文件/etc/apt/sources.list，添加以下源：

>    deb http://ftp.debian.org/debian/ squeeze-updates main

>    deb-src http://ftp.debian.org/debian/ squeeze-updates main

>    deb http://http.us.debian.org/debian stable main

执行`apt-get update`命令更新软件包列表。

* 配置网络

编辑网络配置文件/etc/network/interfaces，添加以太网卡的配置，自动获取IP：

>    auto eth0

>    iface eth0 inet dhcp

如果设置固定IP，添加以下配置：

>    auto eth0

>    iface inet eth0 static

>    address 192.168.1.235

>    netmask 255.255.255.0 

>    network 192.168.1.0

>    broadcast 192.168.1.255

>    gateway 192.168.1.1

* 使用apt-spy选择最优更新源

apt-spy可以帮助我们从众多的Debian更新源中选择最快的服务器。

    # su
    # apt-get install apt-spy
    # apt-spy -d stable -a asia -t 5
    # apt-get update
    
apt-spy命令的具体用法可以通过`man apt-spy`查看。

* 配置中文支持

在Debian上，可以通过dpkg-reconfigure命令配置已安装的软件包。执行`dpkg-reconfigure locales`命令，选中zh_CN支持。

* 安装中文字体

安装文鼎、文泉驿等字体

    # su
    # apt-get install ttf-arphic-uming
    # apt-get install xfonts-intl-chinese
    # apt-get install xfonts-wqy
    
    
* 安装常用工具

安装基本的开发、编译、文档工具。

    # su
    # apt-get install build-essential
    # apt-get install gdb
    # apt-get install autoconf
    # apt-get install automake
    # apt-get install cmake
    # apt-get install libtool
    # apt-get install libboost-dbg
    # apt-get install libboost-doc
    # apt-get install libboost-doc
    # apt-get install libxml2 
    # apt-get install libxml2-dbg 
    # apt-get install libxml2-dev 
    # apt-get install libxml2-doc 
    # apt-get install libxml2-utils
    # apt-get install libmysqlclient15-dev
    # apt-get install manpages-dev
    # apt-get install glibc-doc
    # apt-get install php5
    # apt-get install phpunit
    # apt-get install subversion
    # apt-get install git
    # apt-get install libcrypto++-dev 
    # apt-get install libcrypto++-doc 
    # apt-get install libcrypto++-utils
    # apt-get install ruby
    # apt-get install rake
    # apt-get install scons
    # apt-get install openssl
    # apt-get install openssl-doc
    # apt-get install openssh-server
    # apt-get install openssh-client
    # apt-get install python-openssl 
    # apt-get install python-openssl-dbg 
    # apt-get install python-openssl-doc
    # apt-get install ca-certificates
    # apt-get install lrzsz
    # apt-get install tcpdump
    # apt-get install unzip 
    # apt-get install tree 
    # apt-get install valgrind
    # apt-get install more
    # apt-get install bison
    # apt-get install byacc
    # apt-get install qt4-demos 
    # apt-get install qt4-demos-dbg
    # apt-get install qt4-designer
    # apt-get install qt4-dev-tools
    # apt-get install qt4-doc 
    # apt-get install qt4-doc-html
    # apt-get install qt4-qmake
    # apt-get install qt4-qtconfig
    # apt-get install python-qt4
    # apt-get install python-qt4-dev
    # apt-get install dos2unix

---

EOF




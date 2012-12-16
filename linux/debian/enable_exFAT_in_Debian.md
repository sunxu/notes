# enable exFAT in Debian

---

* 准备

首先安装subversion、scons、libfuse-devel、gcc等工具

    # apt-get install subversion
    # apt-get install scons
    # apt-get install libfuse-dev
    # apt-get install gcc

* 下载exfat

exfat是GNU/Linux下的exFAT系统的一个实现，代码托管在[code.google.com](https://code.google.com/p/exfat/ 'https://code.google.com/p/exfat/')
    
    # svn co http://exfat.googlecode.com/svn/trunk/ exfat-read-only
    
* 编译安装

进入源代码目录，使用scons编译、安装，并挂载安装的模块

    # cd exfat-read-only
    # scons
    # sudo scons install
    # sudo modprobe fuse
    # sudo reboot
    
重启之后就可以使用mount命令挂载exFAT格式的硬盘了。

---

EOF
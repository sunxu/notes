# add ISO image to apt sources

---

* 自动挂载ISO

在/etc/init.d文件夹下，创建文件mountiso。用来在系统启动时，自动挂载ISO文件。在mountiso中写入以下内容：

>    #! /bin/sh

>    ### BEGIN INIT INFO

>    # Provides:          mountiso

>    # Required-Start:    $all

>    # Required-Stop:

>    # Should-Start:

>    # Default-Start:     2 3 4 5 

>    # Default-Stop:

>    # Short-Description: mount debian iso

>    ### END INIT INFO

>    # mount debian iso

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-1.iso /data/debian-iso/apt-source/iso1

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-2.iso /data/debian-iso/apt-source/iso2

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-3.iso /data/debian-iso/apt-source/iso3

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-4.iso /data/debian-iso/apt-source/iso4

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-5.iso /data/debian-iso/apt-source/iso5

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-6.iso /data/debian-iso/apt-source/iso6

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-7.iso /data/debian-iso/apt-source/iso7

>    mount -o loop /data/debian-iso/iso/debian-6.0.6-i386-DVD-8.iso /data/debian-iso/apt-source/iso8

其中ISO文件存放在/data/debian-iso/iso/文件夹中，挂载在/data/debian-iso/apt-source/iso*上。然后给mountiso添加可执行权限，并激活启动脚本：

    # su
    # chmod +x /etc/init.d/mountiso
    # insserv mountiso -v

* 更新sources.list

修改/etc/apt/sources.list文件，在文件尾添加以下内容，并注释掉其他更新源：

>    deb file:/data/debian-iso/apt-source/iso1 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso2 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso3 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso4 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso5 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso6 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso7 squeeze contrib main

>    deb file:/data/debian-iso/apt-source/iso8 squeeze contrib main

* 检索软件包列表

    apt-get update
    
之后通过apt-get或者aptitude安装软件，就会从本地ISO中获取。

---

EOF 

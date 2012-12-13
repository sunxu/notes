# configure wireless network on debian

---

OS:Debian 2.6.32-46

NoteBook:ThinkPad E40

* 查看网卡类型

执行lspci命令，列出所有PCI设备，查看其中的WiFi适配器类型：

    # lspci |grep [n,N]et   
    03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

* 下载compat-wireless驱动

无线网卡类型为RTL8188CE 802.11b/g/n，在[linuxwireless.org](http://linuxwireless.org "linuxwireless.org")上搜索`RTL8188CE`,发现RTL8192CE和RTL8188CE共用同一个驱动。在[http://linuxwireless.org/en/users/Download/stable](http://linuxwireless.org/en/users/Download/stable "linuxwireless.org")上下载驱动compat-wireless-3.6.8-1-sn.tar.bz2。

* 编译安装驱动

执行以下命令，安装驱动：

    # tar xjf compat-wireless-3.6.8-1-sn.tar.bz2
    # cd compat-wireless-3.6.8-1-sn
    # ./scripts/driver-select rtlwifi
    # make
    # sudo make install
    # sudo reboot

* 安装固件

使用dmseg查看系统的启动信息：

    # dmesg | grep 8192
    [    8.209253] rtl8192ce 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
    [    8.209262] rtl8192ce 0000:03:00.0: setting latency timer to 64
    [    8.219698] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
    [    8.234343] rtlwifi: Firmware rtlwifi/rtl8192cfw.bin not available

从dmesg返回的结果来看，驱动rtlwifi使用固件rtlwifi/rtl8192cfw.bin，但是并不存在，因此需要安装该固件。在[www.realtek.com](http://www.realtek.com/default.aspx "realtek.com")上搜索`RTL8188CE`，根据内核版本（`uname -a`）下载压缩包。本机内核为Debian 2.6.32-46，下载的固件为92ce_linux_mac80211_0007.0809.2012.tar.gz。安装固件并重启：

    # tar xzf 92ce_linux_mac80211_0007.0809.2012.tar.gz
    # cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012/
    # sudo cp -r firmware /lib/modules/2.6.32-5-686/
    # sudo reboot

* 启动无线网卡

执行ifconfig启动无线网卡。

    # ifconfig wlan0 up
    
配置好无线连接就可以使用无线上网了。

---

EOF

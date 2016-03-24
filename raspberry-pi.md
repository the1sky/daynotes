#### 树莓派3实战

1、安装系统


    #1  准备一张micro sd卡,注意最新的pi3是这个格式
    #2  格式化，FAT格式（支持大容量）
    #3  下载NOODS，直接copy到sd卡
    #4  把sd卡插入pi3,同时接显示器，鼠标以及键盘
    #5  供电启动，安装系统


2、连接pi3

    #1  用直连网线连接电脑和pi3
    #2  网络共享，选择网线连接的网卡，( mac os下我使用usb转换,选择“usb以太网” )
    #3  ssh pi@192.168.2.2，并输入密码raspberry

3、手动连接wifi

    #1  启动网卡
            ifconfig wlan0  up
    #2  连接wifi,通过直连的方式没有成功,需要继续跟进   ???
            iwconfig wlan0 essid xxx key s:xxxxx
        通过修改配置文件成功
            vim /etc/network/interfaces
            添加:
            iface wlan0 inet dhcp
            wpa-ssid “xxxxx"````
            wpa-psk “xxxxx"
    #3  重启网卡,修改配置文件后需要
            /etc/init.d/networking restart

4、DNS配置

    #1 成功连接wifi后发现能通过ip访问当不能通过域名访问,第一时间想到DNS,配置如下:
            echo "nameserver 8.8.8.8" > /etc/resolv.conf

5、wifi hotspot

    #1  建立热点
            //todo
####kali研究

#####parallels desktop 11安装kali问题

    #1  无法安装linux-headers-4.3.0-kali1-amd64

        需要升级到linux-headers-4.4.0-kali1-amd64

    #2  升级到linux-headers-4.4.0-kali1-amd64步骤

        *1  sources.list源,仅需要这两个地址:

            deb http://http.kali.org/kali kali-rolling main contrib non-free
            deb-src http://http.kali.org/kali kali-rolling main contrib non-free

            官方参考:
                http://docs.kali.org/general-use/kali-linux-sources-list-repositories
        *2  apt-get clean
        *3  apt-get update
        *4  apt-get upgrade -y
        *5  apt-get dist-upgrade -y
        *6  reboot

        *7  重启后,利用uname -r查看确认
        *8  安装parallel

#####安装parallel tool权限问题

    #1  卸载光盘
        umount  /media/cdrom0

    #2  重新挂载
        mount -o exec /media/cdrom0

    #2  安装
        cd /media/cdrom0
        ./install

#####大功告成,在mac上通过parallels完美安装kali


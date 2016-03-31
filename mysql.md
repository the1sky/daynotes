####mysql

#####<s>emoji表情与utf8mb4</s>

######说明

    utf-8只支持1-3字节

    多了,怎办?

    utf8mb4
######配置

    vim my.cnf

    设置如下:

    [client]
    default-character-set=utf8mb4

    [mysql]
    default-character-set=utf8mb4

    [mysqld]
    character-set-server=utf8mb4
    collation-server=utf8mb4_bin

######查看

    show variables like 'collation_%';
    show variables like 'character_set_%';

#####重启

    service mysqld restart
    /etc/init.d/mysqld restart



#####攻城攻心
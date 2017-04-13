# mysql 资料备份及恢复

起因：malls 表中数据被误删了。顺带也删掉了关联的 orders 表中的数据。

工具：阿里云数据库有周期性的备份机制，下载了最近的备份文件，解压后是一堆 frm 和 ibd 文件

阿里云文档推荐使用 xtrabackup 软件进行恢复工作。下载尝试，无果，弃之。

于是 google 如何用 ibd 文件恢复数据，果然是可以试一试的，直觉都好灵验的。

针对：innodb engine

坑点：
    1: 要确保导入导出的 mysql version 尽量相同。【同 5.6.x 】

    2: 执行 `show variables like '%innodb_file_per_table%';` 查看 innodb_file_per_table 是否等于 "1" 或者 "on".

        可以设置，在 my.conf 文件里面设置
        ```sql
        [mysqld]
        innodb_file_per_table=1

        或者

        set GLOBAL innodb_file_per_table=1;
        ```

恢复过程[参考](http://www.longlong.asia/2015/11/21/mysql-restore-ibd.html)

    # 新建一个数据库
    create database glz;

    use glz;

    # 新建与要恢复的表相同结构的表(可以直接去导出表的结构)
    SET FOREIGN_KEY_CHECKS = 0;

    DROP TABLE IF EXISTS  `malls`;
    CREATE TABLE `malls` (
    `id` int(11) NOT NULL AUTO_INCREMENT,
    `name` varchar(30) NOT NULL,
    `currency` tinyint(4) NOT NULL DEFAULT '0',
    `price` decimal(10,2) DEFAULT NULL,
    `count` bigint(20) NOT NULL,
    `icon` varchar(50) NOT NULL,
    `abstract` varchar(80) NOT NULL,
    `descript` text,
    `supply_status` tinyint(4) NOT NULL DEFAULT '0',
    `sale_status` tinyint(4) NOT NULL DEFAULT '0',
    `c_f_id` bigint(20) NOT NULL DEFAULT '0',
    `c_s_id` bigint(20) NOT NULL DEFAULT '0',
    `area` varchar(300) DEFAULT NULL,
    `distribution` varchar(80) NOT NULL,
    `service` varchar(80) DEFAULT NULL,
    `category_first` mediumint(9) NOT NULL,
    `category_id` mediumint(9) NOT NULL,
    `types` tinyint(4) NOT NULL DEFAULT '0',
    `quota` mediumint(9) DEFAULT NULL,
    `courier_fees` mediumint(9) NOT NULL DEFAULT '0',
    `orders_count` bigint(20) NOT NULL DEFAULT '0',
    `prompt` varchar(80) NOT NULL,
    `alipay` tinyint(1) DEFAULT '0',
    `created_at` datetime NOT NULL,
    `updated_at` datetime NOT NULL,
    `amount` int(11) NOT NULL DEFAULT '0',
    `latest_version` tinyint(1) NOT NULL DEFAULT '0',
    `reference_id` int(11) NOT NULL DEFAULT '1',
    `reference_type` varchar(12) NOT NULL DEFAULT 'Staff',
    `c_t_id` int(11) NOT NULL DEFAULT '0',
    `c_z_id` int(11) NOT NULL DEFAULT '0',
    `express_id` int(11) NOT NULL DEFAULT '0',
    PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=556 DEFAULT CHARSET=utf8;

    SET FOREIGN_KEY_CHECKS = 1;

    > 这时会在 /var/lib/mysql/glz/ 目录下生成 malls.frm(表结构) 和 malls.ibd(实际数据) 两个文件。

    # 将此表实际数据移出表空间(通过 mysql 删除上面的 malls.ibd 文件)
    alter table glz.malls discard tablespace;

    # 复制新数据文件到表空间目录下
    cp /backup/malls.ibd /var/lib/mysql/glz/

    # 将新数据导入表空间
    alter table glz.malls import tablespace;


    # 如果一切正常，就完了。


# 工具 （MySQLWorkbench)
    可以导出 insert statement


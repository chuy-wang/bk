### MySQL主从复制的实现原理

1. 异步复制
2. 半同步复制

#### 配置步骤

在master服务器上的操作

1. 开启binlog（必须）开启gtid（可选 v5.6以上）
2. 建立同步所用的数据库账号
3. 使用master_data参数备份数据库
4. 吧备份文件传输到slave服务器

在slave服务器上的操作

1. 开启binlog（可选）开启gtid（可选）
2. 恢复master上的备份数据库
3. 使用change master配置链路
4. 使用start slave启动复制

### MySQL主从复制的操作

#### 异步复制

```mysql
select @@version;-- 主从各自执行该命令确认版本是否可用
show variables like 'log_bin%';	-- 主服务器执行，检查是否开启binlog
show variables like 'gtid_mode'; -- 主服务器执行，检查是否开启gtid
create user repl@'xxx' identified by 'xxxx' -- 创建同步用账号

mysqldump --single-transaction -uroot -p --routinges --triggers --events --master-data=2 --all-databases > master.sql -- 备份主库

mysql -uroot -p < master.sql -- 从库恢复主库数据
change master to master_host='xxx.xx.xx' master_log_file='xxxxx' master_log_pos=xxx; --设置从服务器开始同步的位置
start slave user='xxx' password='xxxx'; -- 从服务器开启
```

#### 半同步复制

```mysql
install plugin rpl_semi_sync_master soname 'semisync_master.so'; -- master安装半同步插件
show plugins; -- 检查安装是否成功
show variables like 'rpl%'; -- 查看半同步配置
set persist rpl_semi_sync_master_enabled=on; -- 启动半同步

install plugin rpl_semi_sync_slave soname 'semisync_slave.so'; -- slave安装半同步插件
set persist rpl_semi_sync_slave_enabled=on; -- 启动半同步

stop slave io_thread;
start slave io_thread user='xxx' password='xxxx'; -- 重启复制链路

show global status like 'rpl%'; -- 查看启动状态
```




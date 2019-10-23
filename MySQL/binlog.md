### 作用

记录所有对数据库中数据的修改

基于时间点的备份和恢复

主从复制

```ini
log-bin[=base_name] #默认存储在MySQL数据目录中，以机器名为前缀，v5.7之后拆分为两个配置项 log_bin log_bin_basename
binlog_format=[ROW|STATEMENT|MIXED] #v5.7之前默认为STATEMENT，v5.7之后默认ROW格式，如果进行多行修改，会生成同样的行数
binlog_row_image=[FULL|MINIMAL|NOBLOB] #MINIMAL只会记录被修改的值，NOBLOB记录出blob之外的修改
binlog_rows_query_log_events=[NO|OFF]
log_slave_updates=[NO|OFF]
sync_binlog=[1|0]

#清理日志
expire_log_days=days
```

```mysql
flush logs; -- 刷新日志
mysqlbinlog

PURGE BINARY LOGS TO 'mysql-bin.010';
PURGE BINARY LOGS BEFORE '2008-04-02 22:22:22';
```


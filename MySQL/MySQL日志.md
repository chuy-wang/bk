### MySQL常用的日志

| 日志名称                     | 作用                                                      |
| ---------------------------- | --------------------------------------------------------- |
| 错误日志（error_log）        | 记录MySQL在启动、运行或停止时出现的问题                   |
| 常规日志（general_log）      | 记录所有发行MySQL的请求（由于数据量庞大，不建议随时开启） |
| 慢查询日志（slow_query_log） | 记录符合条件的查询                                        |
| 二进制日志（binary_log）     | 记录全部有效的数据修改日志                                |
| 中继日志（relay_log）        | 用户主从复制，临时存储从主服务器同步的二进制日志          |

### 错误日志

```ini
log_error=$mysql/sql_log/mysql-error.log
log_error_verbosity=[1,2,3]  #mysql 5.7新增
# 1 error message
# 2 error and warning message
# 3 error warning and note message

log_error_services=[日志服务组件；日志服务组件] #mysql 8.0新增
# log_filter_internal 默认的日志过滤组件，依赖log_error_verbosity
# log_sink_internal 默认的日志输出组件，依赖log_error
# log_sink_json	将错误日志输出到json文件
# log_sink_syseventlog 将错误日志暑促到系统日志文件
```

### 常规日志

分析客户端发送到MySQL的实际请求

```ini
general_log=[NO|OFF]
general_log_file=$mysql/sql_log/general.log
log_output=[FILE|TABLE|NONE]
```



### 慢查询日志

将执行成功并符合条件的查询记录到日志中

找的需要优化的SQL

```ini
slow_query_log=[NO|OFF]
slow_query_log_file=$mysql/sql_log/slowlog.log
long_query_time=xx秒
log_queries_not_using_indexes=[ON|OFF]	#没有用到索引的
log_slow_admin_statements=[ON|OFF] #记录管理命令
log_slow_slave_statements=[NO|OFF]	#主从同步用
```


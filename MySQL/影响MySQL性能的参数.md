|                 | 参数                           | 说明                                                         |
| --------------- | ------------------------------ | ------------------------------------------------------------ |
| 服务器 配置参数 | max_connections                | 设置MySQL允许访问的最大链接数（设置过大会内存不足）          |
|                 | interactive_timeout            | 设置交互连接的timeout时间                                    |
|                 | wait_timeout                   | 设置非交互连接的timeout时间                                  |
|                 | max_allowed_packet             | 控制mysql可以接收的数据包的大小（主从同步时不一致可能会引起失败） |
|                 | sync_binlog                    | 表示没写多少次缓冲会想磁盘同步一次binlog（master 1）         |
|                 | sort_buffer_size               | 设置每个会话使用的排序缓存区的大小                           |
|                 | join_buffer_size               | 设置每个会话所使用的连接缓冲的大小                           |
|                 | read_buffer_size               | 指定了当对一个MyIsam进行表扫描时所分配的读缓冲池的大小       |
|                 | read_rnd_buffer_size           | 设置控制索引缓冲区的大小                                     |
|                 | binlog_cache_size              | 设置每个会话用于缓存未提交的事务缓存大小                     |
| 存储引擎参数    | Innodb_flush_log_at_trx_commit | 0：每秒进行一次重做日志的磁盘刷新操作 1：每次事务提交都会刷新事务日志到磁盘 2：每次事务提交写入系统缓存每秒想磁盘刷新一次 |
|                 | innodb_buffer_pool_size        | 设置innodb缓冲池的大小，应为系统可用内存的75%                |
|                 | innodb_buffer_pool_instances   | Innodb缓冲池的实例个数，每个实例的大小为总缓冲池大小/实例个数 |
|                 | innodb_file_per_table          | 设置每个表独立使用一个表空间文件                             |


### 背景

提到 MySQL， 我们不得不说说其两大重要的时间点

- 2008 年 Sun 收购 MySQL AB
- 2010 年 Oracle 收购 Sun

在 MySQL 两次易主的过程中，开发者们普遍担心某一天 MySQL 会成为一个非开源的收费版本，所以在此期间出现了很多类 MySQL 的 RDBMS。然而到目前为止，主要有两个久经考验的 RDBMS 分别为：`Percona server for MySQL` 和 `MariaDB`

### MySQL常见发行版本

####1. MySQL官方版本

- 企业版
- 社区版

#### 2. Percona server for MySQL

Percona Server是MySQL咨询公司Percona发布的性能最接近MySQL企业版的MySQL产品。Percona公司在MySQL数据库优化方面做了非常多的工作，以至于Percona Server数据库是MySQL众多分支中，在高负载、高并发情况下表现非常突出

特性主要包括

- 完全兼容 MySQL 协议
- Bug 修复
- 性能优化
- 支持 MySQL 社区版和企业版功能特性
- 丰富的性能诊断工具

#### 3. MariaDB

起初MySQL之父Monty在1979年写下MySQL的第一行代码，后来逐渐创建起MySQL公司，后将其以10亿美金卖给Sun，结果Sun又把MySQL转手卖给Oracle，Monty愤而出走，以MySQL5.5为基础创造了MariaDB数据库，这样就诞生出了MySQL分支里知名度最高的一个衍生版



### 各发行版之间的区别和特点

|            | MySQL                                 | Percona MySQL                         | MariaDB                           |
| :--------: | ------------------------------------- | ------------------------------------- | --------------------------------- |
| 服务器特性 | 开源                                  | 开源                                  | 开源                              |
|            | 支持分区表                            | 支持分区表                            | 支持分区表                        |
|            | InnoDB                                | XtraDB                                | XtraDB                            |
|            | 企业版提供监控工具（社区版不提供）    | Percona Monitor 工具                  | Monyog                            |
|   高可用   | 基于日志点的复制                      | 基于日志点的复制                      | 基于日志点的复制                  |
|            | 基于gtid的复制                        | 基于gtid的复制                        | 基于gtid的复制（但是不兼容MySQL） |
|            | MGR                                   | MGR & PXC                             | Galera Cluster                    |
|            | MySQL Router                          | ProxySQL                              | MaxScale                          |
|    安全    | 企业版防火墙                          | ProxySQL FireWall                     | MaxScale FireWall                 |
|            | 企业版用户审计                        | 审计日志                              | 审计日志                          |
|            | 用户密码生命周期                      | 用户密码生命周期                      | -                                 |
|            | sha256_password caching_sha2_password | sha256_password caching_sha2_password | ed22519 sha256_password           |
| 开发及管理 | 窗口函数（version 8.0）               | 窗口函数（version 8.0）               | 窗口函数（version 10.2）          |
|            | -                                     | -                                     | 基于日志回滚                      |
|            | -                                     | -                                     | 支持记在表中的记录修改            |
|            | super read_only                       | super read_only                       | -                                 |
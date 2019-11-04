###MMM和MHA架构的作用

- 对主从复制集群中的MASTER的健康进行监控
- 当MASTER宕机后吧写VIP迁移到新的MASTER
- 重新配置集群中的其它slave对新的MASTER同步


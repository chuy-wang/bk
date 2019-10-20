### SQL_MODE

配置MySQL处理SQL的方式

```mysql
set[session|global|persist] sql_mode='xxx,xxxx,xxx';
[mysqld] sql_mode='xxx';
sql_mode='ANSI'; -- 宽松模式
```

### 常用的SQL MODE

| SQL_MODE                                    | 说明                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| ONLY_FULL_GROUP_BY                          | 对GROUP BY聚合操作，如果出现在SELECT中的列、HAVING或者ORDER BY子句的非聚合列，没有在GROUP BY中出现，那么这个SQL语法检查报错 |
|                                             | 禁止用双引号来引用字符串                                     |
| REAL_AS_FLOAT                               | real作为float的同义词                                        |
| PIPES_AS_CONCAT                             | 将\|\|视为字符串的链家操作符而非 或 运算符                   |
| ANSI                                        | 宽松模式                                                     |
| `STRICT_TRANS_TABLES` / `STRICT_ALL_TABLES` | 在事务存储引擎 / 所有存储引擎上启用严格模式出现，那么这个SQL语法前程报错 |
| ERROR_FOR_DIVISION_BY_ZERO                  | 不允许0作为除数                                              |
| NO_AUTO_CREATE_USER (V5.6 V5.7)             | 在用户不存在时不允许grant语句自动创建                        |
| `NO_ZERO_IN_DATE` / `NO_ZERO_DATE`          | 日期数据内 / 日期数据不能含0 （严格模式下生效）              |
| NO_ENGINE_SUBSTITUTION                      | 当指定的存储引擎不可用时报错                                 |
| TRADITIONAL                                 | 严格模式                                                     |


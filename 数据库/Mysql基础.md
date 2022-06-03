# MySQL基础

## 查询

![img](Mysql基础.assets/0d2070e8f84c4801adbfa03bda1f98d9.png)

> ==MySQL 8.0 版本直接将查询缓存的整块功能删掉了==

## 日志模块

### redo log

> MySQL 里经常说到的 WAL 技术，WAL 的全称是 Write-Ahead Logging，它的关键点就是先写日志，再写磁盘。

有了 redo log，InnoDB 就可以保证即使数据库发生异常重启，之前提交的记录都不会丢失，这个能力称为 crash-safe。==InnoDB独有==

### binlog

1. redo log 是 InnoDB 引擎特有的；binlog 是 MySQL 的 Server 层实现的，所有引擎都可以使用。
2. redo log 是物理日志，记录的是“在某个数据页上做了什么修改”；binlog 是逻辑日志，记录的是这个语句的原始逻辑，比如“给 ID=2 这一行的 c 字段加 1 ”。
3. redo log 是循环写的，空间固定会用完；binlog 是可以追加写入的。“追加写”是指 binlog 文件写到一定大小后会切换到下一个，并不会覆盖以前的日志。

![img](Mysql基础.assets/2e5bff4910ec189fe1ee6e2ecc7b4bbe.png)
### sysbench.config文件

```shell
mysql-host=10.226.132.104
mysql-port=14000
mysql-user=root
mysql-password=123456
mysql-db=sbtest
time=600
report-interval=10
```

创建数据库

```my
 create database sbtest
```

设置乐观事务模式

```shell
 set global tidb_disable_txn_auto_retry = off; 
 set global tidb_txn_mode="optimistic"; 
```

导入数据

```shell
sysbench --config-file=sysbench.config oltp_point_select --threads=128  --tables=32 --table-size=100000 prepare
```

数据导入完毕后，再设置回悲观模式 

```shell
 set global tidb_disable_txn_auto_retry = on; 
 set global tidb_txn_mode="pessimistic"; 
```

单点查询

```shell
sysbench --config-file=sysbench.config oltp_point_select --threads=128  --tables=32 --table-size=100000 run
```

更新索引测试

```shell
sysbench --config-file=sysbench.config oltp_update_index --threads=128  --tables=32 --table-size=100000 run
```

只读测试

```shell
sysbench --config-file=sysbench.config oltp_read_only --threads=128  --tables=32 --table-size=100000 run
```


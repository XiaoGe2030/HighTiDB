# sysbench

config文件

```shell
mysql-host=10.226.132.104
mysql-port=14000
mysql-user=root
mysql-password=123456
mysql-db=sbtest
time=600
report-interval=10
```



prepare 

```shell
sysbench --config-file=sysbench.config oltp_point_select  --threads=128  --tables=32 --table-size=1000000 prepare
```

单点查询

```shell
sysbench --config-file=sysbench.config oltp_point_select  --threads=128  --tables=32 --table-size=1000000 run
```

更新索引

```shell
sysbench --config-file=sysbench.config oltp_update_index   --threads=128  --tables=32 --table-size=1000000 run
```

只读测试

```shell
sysbench --config-file=sysbench.config oltp_read_only   --threads=128  --tables=32 --table-size=1000000 run
```


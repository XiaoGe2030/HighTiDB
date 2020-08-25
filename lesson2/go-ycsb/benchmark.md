# go-ycsb测试

准备数据

```shell
./bin/go-ycsb load mysql -P workloads/workloada -p recordcount=100000 -p mysql.host=10.226.132.104 -p mysql.port=14000 -p mysql.password=123456  --threads 256
```

测试数据

```she
./bin/go-ycsb run mysql -P workloads/workloada -p recordcount=100000 -p mysql.host=10.226.132.104 -p mysql.port=14000 -p mysql.password=123456  --threads 256
```



准备数据

```shell
./bin/go-ycsb load  mysql -P workloads/workloadb -p recordcount=1000000 -p mysql.host=10.226.132.104 -p mysql.port=14000 -p mysql.password=123456  --threads 256
```

测试数据

```shell
./bin/go-ycsb run mysql -P workloads/workloadb -p recordcount=100000 -p mysql.host=10.226.132.104 -p mysql.port=14000 -p mysql.password=123456  --threads 256
```


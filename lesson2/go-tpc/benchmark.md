# go-tpc测试

准备数据

```shell
./bin/go-tpc tpcc -H 10.226.132.104 -P 14000 -p 123456 -D tpcc --warehouses 8 prepare -T 8
```

测试tpcc

```shell
./bin/go-tpc tpcc -H 10.226.132.104 -P 14000 -p 123456 -D tpcc --warehouses 8 run --time 3m  --threads 512
```

准备数据

```shell
./bin/go-tpc tpch prepare -H 10.226.132.104 -P 14000 -p 123456 -D tpch --sf 1 --analyze
```

测试tpch

```shell
./bin/go-tpc tpch run  -H 10.226.132.104 -P 14000 -p 123456 -D tpch --sf 1 --time 3m
```


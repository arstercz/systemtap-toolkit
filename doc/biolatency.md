## biolatency

获取块设备 I/O 延迟的分布. 如下所示:
```
# stap biolatency.stp 
Tracing block I/O... Hit Ctrl-C to end.
^C
bio latency (ns):
   value |-------------------------------------------------- count
  131072 |                                                    0
  262144 |                                                    0
  524288 |@@                                                  5
 1048576 |@@                                                  4
 2097152 |@@@@@@@@@@@@@@@@@@@@@@@@                           49
 4194304 |@@@@@@@@@@@@@@@@@@@@@@@@@@@                        55
 8388608 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@          82
16777216 |@@@@@@@@@@@@@@@@@@                                 37
33554432 |                                                    0
67108864 |                                                    0
```

左边为时间延迟(ns)的分布, 右边为请求的次数.

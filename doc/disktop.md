## disktop

以降序方式显示当前 I/O 读写的进程, 包含设备及读写类型. 如下所示:

```
# stap src/io/disktop.stp 

Tue Oct 29 20:12:00 2019 CST, Average:   7Kb/sec, Read:      39Kb, Write:      0Kb

     UID      PID     PPID                       CMD   DEVICE    T        BYTES
       0    67369    66787                       top     sda2    R        37430
       0    67368    66787                      bash     sda2    R         2502
       0    67369    66787                      bash     sda2    R          788
```

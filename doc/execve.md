## execve

打印所有执行 `execve` 系统调用的信息.

```
# stap -r `uname -r` execve.stp -m execve.ko -p4
Truncating module name to 'execve'
execve.ko

# staprun execve.ko 
Enter Ctrl-c to end...
TIME                            UID    PID   PPID             COMM ARGS
Wed Oct 30 10:38:59 2019 CST      0  86842  86289           uptime uptime
Wed Oct 30 10:39:01 2019 CST      0  86843  86289               ls ls --color=auto
Wed Oct 30 10:39:01 2019 CST      0  86845  86844               sh /bin/sh -c /usr/lib64/sa/sa1 1 1
Wed Oct 30 10:39:01 2019 CST      0  86845  86844              sa1 /bin/sh /usr/lib64/sa/sa1 1 1
Wed Oct 30 10:39:01 2019 CST      0  86846  86845             date date +%d
Wed Oct 30 10:39:01 2019 CST      0  86847  86845             date date +%Y%m
```

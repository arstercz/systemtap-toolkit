## iotop

获取 io 占用最高的前 15 个进程, 每 5s 刷新一次, 不显示设备：

```
# stap src/io/iotop.stp 
Get the top 15 io of the processes every 5000ms...
Process                 PID     Read(KB)    Write(KB)
top                   67369          135           22
sshd                  43612           26           23
redis-server          35307           18            0
systemd-udevd          1613            0            0
systemd-udevd         67391            0            0
stapio                67390            0            0
in:imjournal           3386            0            0
```

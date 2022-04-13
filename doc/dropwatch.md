## dropwatch

查看数据包被 `drop` 的信息:

```
# stap -r `uname -r` dropwatch.stp -m dropwatch.ko -p4                    
Truncating module name to 'dropwatch'
dropwatch.ko

# staprun dropwatch.ko 
Monitoring for dropped packets


2 packets dropped at 0xffffffff8a4f9b48
2 packets dropped at 0xffffffff8a4fa33a
^CStopping dropped packet monitor
```

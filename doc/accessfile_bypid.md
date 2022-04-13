## accessfile_bypid

显示指定进程读写的文件信息, 按读写次数降序输出:
```
# stap -r `uname -r` accessefile_bypid.stp -m accessefile_bypid.ko -p4 
Truncating module name to 'accessefile_bypid'
accessefile_bypid.ko

# staprun accessefile_bypid.ko pid=`pidof redis-server`                
Enter Ctrl-C to end.
Tracing pid 81763 
^C
=== Top 15 file read/write ===
#1: 34 times, 12478 bytes read/write in file stat.
#2: 5 times, 302 bytes read/write in file redis.log.
#3: 1 times, 18 bytes read/write in file TCP.
#4: 1 times, 77 bytes read/write in file temp-81763.rdb.
```

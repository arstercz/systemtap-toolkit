## fsslower

获取读写延迟较大的进程, 默认阈值为 10ms:
```
# stap -r `uname -r` fsslower.stp -m fsslower.ko -p4
Truncating module name to 'fsslower'
fsslower.ko

# staprun fsslower.ko min_ms=3
Tracing FS sync reads and writes slower than 3 ms... Hit Ctrl-C to end.
TIME     PID    COMM             FUNC           SIZE     LAT(ms)
10:17:25 82742  tail             do_sync_read   8192           4
10:17:25 82739  redis-shutdown   do_sync_read   128            7
10:17:25 82745  tail             do_sync_read   8192           4
10:17:25 82739  redis-shutdown   do_sync_read   128            7
10:17:25 82748  tail             do_sync_read   8192           3
10:17:25 82739  redis-shutdown   do_sync_read   128            6
```

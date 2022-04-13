## tcp_recv_queue

显示指定 tcp 端口的 recv 状态的队列信息, 必须通过 `destport` 执行端口:
```
# stap -r `uname -r` tcp_recv_queue.stp -m tcp_recv_queue.ko -p4
Truncating module name to 'tcp_recv_queue'
tcp_recv_queue.ko

# staprun tcp_recv_queue.ko destport=22
Enter Ctrl-C to end.
Tracing the TCP receive queues for packets to the port 22
^C
=== Distribution of First-In-First-Out Latency (us) in TCP Receive Queue ===
min/avg/max: 45/46/48
value |-------------------------------------------------- count
    8 |                                                   0
   16 |                                                   0
   32 |@@                                                 2
   64 |                                                   0
  128 |                                                   0
```

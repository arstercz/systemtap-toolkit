## tcp_retrans

查看指定 tcp 端口的数据包重传信息, 支持 `ipv4` 和 `ipv6`, 使用 destport 指定端口:

```
# stap -r `uname -r` tcp_retrans.stp -m tcp_retrans.ko -p4
Truncating module name to 'tcp_retrans'
tcp_retrans.ko

# staprun tcp_retrans.ko destport=80
=> Only capture destination port: 80

Printing tcp retransmission, Enter Ctrl-C to end.

Wed Oct 30 11:56:12 2019 CST 10.3.254.119:49896 -> 10.3.254.107:80 state:TCP_SYN_SENT rto:0 -> 1000 ms
Wed Oct 30 11:56:13 2019 CST 10.3.254.119:49896 -> 10.3.254.107:80 state:TCP_SYN_SENT rto:1000 -> 2000 ms
Wed Oct 30 11:56:15 2019 CST 10.3.254.119:49896 -> 10.3.254.107:80 state:TCP_SYN_SENT rto:2000 -> 4000 ms
```

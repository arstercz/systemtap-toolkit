## tcp_conn

记录 tcp 的连接信息, 支持 `ipv4` 和 `ipv6`, 可以设置 `destport` 仅抓取指定的端口:
```
# stap -r `uname -r` tcp_conn.stp -m tcp_conn.ko -p4
Truncating module name to 'tcp_conn'
tcp_conn.ko

# staprun tcp_conn.ko 
                        TIME   EUID    UID    GID              CMD    PID   PORT IP_SOURCE
Wed Oct 30 11:46:12 2019 CST    996    996    994     redis-server  83155   6379 10.1.1.19
Wed Oct 30 11:46:29 2019 CST      0      0      0             sshd  28552     22 fe80:0000:0000:0000:0222:19ff:fe64:63c2
Wed Oct 30 11:46:34 2019 CST      0      0      0             sshd  28552     22 fe80:0000:0000:0000:0222:19ff:fe64:63c2
^C

# staprun tcp_conn.ko destport=22  # 仅记录 22 端口的连接
=> Only capture port: 22

                        TIME   EUID    UID    GID              CMD    PID   PORT IP_SOURCE
Wed Oct 30 11:49:06 2019 CST      0      0      0             sshd  28552     22 fe80:0000:0000:0000:0222:19ff:fe64:63c2
Wed Oct 30 11:49:15 2019 CST      0      0      0             sshd  28552     22 10.1.1.19
```


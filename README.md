## systemtap-toolkit

[systemtap](https://sourceware.org/systemtap/) 在 Linux 系统排错方面一直占据着很重要的角色, 其提供了很成熟的调试符号及复杂的探针处理程序, 可以在系统调用, 用户空间及内核空间几个方面实现细粒度的跟踪分析, 更详细的介绍可以参考 [dynamic-tracing](https://openresty.org/posts/dynamic-tracing/). `systemtap-toolkit` 工具集则是在此基础上，搜集并整理的一些常用的分析工具, 方便对 `Linux` 系统中一些疑难问题的跟踪处理. 下面的工具列表部分来源于网络, 进行了简单修改以支持 `staprun` 方式运行时可以指定额外的参数. 具体见参考部分.


## 工具列表

### io

[biolatency.stp](doc/biolatency.md) 获取块设备 I/O 延迟的分布.  
[disktop.stp](doc/disktop.md) 显示当前 I/O 读写的进程.  
[iotop.stp](doc/iotop.md) 取 io 占用最高的前 15 个进程.  

### fs

[accessfile_bypid](doc/accessfile_bypid.md) 显示指定进程读写的文件信息.  
[fsslower.stp](doc/fsslower.md) 获取读写延迟较大的进程.  


### net

[dropwatch.stp](doc/dropwatch.md) 查看数据包被 `drop` 的信息.  
[tcp_conn.stp](doc/tcp_conn.md) 记录 tcp 的连接信息.  
[tcp_recv_queue.stp](doc/tcp_recv_queue.md) 显示指定 tcp 端口的 recv 状态的队列信息.  
[tcp_retrans.stp](doc/tcp_retrans.md) 查看指定 tcp 端口的数据包重传信息.  

### syscall

[execve.stp](doc/execve.md) 获取所有执行 `execve` 系统调用的进程信息.  
[threads_times.stp](doc/threads_times.md) 统计线程在用户态和内核态运行的时间百分比.  
[topsys.stp](doc/topsys.md) 显示系统调用的信息.  

## 编译运行说明

由于 systemtap 没有集成到内核主版本中, 再加上其可以动态的编译成 Linux 的内核模块, 因此实际的使用中需要我们在系统中安装内核版本对应的 `header` 以及 `debug` 相关的开发包. 以 `RedHat/Centos` 系统为例, `systemtap` 工具脚本的运行需要以下安装包:
```
kernel-3.10.0-957.27.2.el7.x86_64
kernel-headers-3.10.0-957.27.2.el7.x86_64
kernel-devel-3.10.0-957.27.2.el7.x86_64
kernel-debuginfo-3.10.0-957.27.2.el7.x86_64
kernel-debuginfo-common-x86_64-3.10.0-957.27.2.el7.x86_64
systemtap-4.0-9.el7.x86_64
```

在通过 `stap` 运行工具的时候需要进行以下 5 个阶段:
```
+----------+    +----------+    +-------------+    +----------+    +------+
|  解析脚本 | -> |  处理分析  | -> | 转为 C 代码  | -> |  编译模块 | -> | 运行  |
+----------+    +----------+    +-------------+    +----------+    +------+
```


如果系统安装了对应内核版本的 `debuginfo, debuginfo-common` 开发包, 可以通过以下两种方式运行工具:

#### 直接运行

```bash
# stap tcp_conn.stp
                        TIME   EUID    UID    GID              CMD    PID   PORT                               IP_SOURCE
Tue Oct 29 19:48:11 2019 CST    996    996    994     redis-server  35307   6379                            10.3.254.119
```
#### 编译模块运行

编译为内核模块后, 通过 `staprun` 方式运行, 如果其他主机的内核版本和编译模块所在的主机相同, 可以直接拷贝模块到其他系统中使用 `staprun` 运行:
```bash
# stap -r `uname -r` tcp_conn.stp -m tcp_conn.ko -p4  #第四阶段
Truncating module name to 'tcp_conn'
tcp_conn.ko

# staprun tcp_conn.ko destport=6379
=> Only capture port: 6379

                        TIME   EUID    UID    GID              CMD    PID   PORT                               IP_SOURCE
Tue Oct 29 19:52:52 2019 CST    996    996    994     redis-server  35307   6379                            10.3.254.119
```

这种方式适合线上系统的排错, 如下所示, 以内核模块方式运行线上系统仅需要以下安装包:
```
kernel-3.10.0-957.27.2.el7.x86_64
kernel-headers-3.10.0-957.27.2.el7.x86_64
kernel-devel-3.10.0-957.27.2.el7.x86_64
systemtap-runtime-4.0-9.el7.x86_64
```

## 参考

[systemtap](https://sourceware.org/systemtap/)  
[systemtap-lwtools](https://github.com/brendangregg/systemtap-lwtools)  
[youzan-systemtap-toolkit](https://github.com/youzan/systemtap-toolkit/)  
[openresty-systemtap-toolkit](https://github.com/openresty/openresty-systemtap-toolkit)  


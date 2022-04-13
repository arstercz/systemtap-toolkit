## topsys

显示系统调用的信息, 按调用次数降序输出:
```
# stap -r `uname -r` topsys.stp -m topsys.ko -p4                  
Truncating module name to 'topsys'
topsys.ko

# staprun topsys.ko 
                  SYSCALL      COUNT
                     read        134
                    close         70
                     open         64
               epoll_wait         56
                    ppoll         31
                    fcntl         22
                   munmap         18
                     stat         15
                    fstat         13
                     mmap         13
                 pselect6         10
                   select          5
                   unlink          4
                    futex          3
            clock_gettime          3
          timerfd_settime          3
                epoll_ctl          2
                    wait4          2
                nanosleep          1
                ftruncate          1
```

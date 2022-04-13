## thread_times

统计线程在用户态和内核态运行的时间百分比, 每 5 秒输出一次:
```
# stap -r `uname -r` thread_times.stp -m thread_times.ko -p4                          
Truncating module name to 'thread_times'
thread_times.ko

# staprun thread_times.ko 
            comm   tid   %user %kernel (of 17325 ticks)
      swapper/14     0   0.00%  28.85%
      swapper/15     0   0.00%  28.85%
       swapper/8     0   0.00%  11.25%
       swapper/3     0   0.00%   9.17%
       swapper/1     0   0.00%   8.18%
      swapper/12     0   0.00%   4.98%
       swapper/0     0   0.00%   1.86%
      swapper/11     0   0.00%   1.50%
      swapper/18     0   0.00%   1.07%
       swapper/9     0   0.00%   0.53%
       swapper/2     0   0.00%   0.44%
       swapper/5     0   0.00%   0.35%
       swapper/7     0   0.00%   0.35%
      swapper/10     0   0.00%   0.35%
      swapper/13     0   0.00%   0.35%
      swapper/22     0   0.00%   0.35%
       swapper/4     0   0.00%   0.21%
       swapper/6     0   0.00%   0.17%
```

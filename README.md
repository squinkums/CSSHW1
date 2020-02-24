# Computer_Systems_HW1

**Part 1**

To read from the buffer, I have created a vector of ints that is the size of the amount of bytes being read divided by the size of ints in C++ (4 bytes), made a variable entitled "x" of type int, and then iterated through the buffer, copying one value to 'x' each time. In order to trick the prefetcher, the strategy of which was helped by Eitan and a fellow student in lab, I made a second vector of indices that is the same size as the buffer. Then, for every read through the buffer, the indices vector was shuffled beforehand and the value buffer[indices[iterator]] was copied to 'x'. I used the "-o3" flag when compiling for the fastest code available. I also experimented with using the "-ofast" flag, yet that yielded similar results. I went with 100 tests in order to both ensure fast runs in the result, but not take forever with more tests.

**Part 2**

Here is the graph of the results of the program:
![Chart](https://github.com/squinkums/Computer_Systems_HW1/blob/master/hw1chart.png)

**Part 3**

       **1.** From looking at the graph, there appears to be an increase going from 65 KB to 131 KB, so I would say that the cache size is around 65KB. The graph is monotonous and appears to be a smooth step function thanks to the jump from 2097KB to 8388KB.
       **2.** I did not get these numbers. My read from an L1 cache definitely took longer by a factor of at least 0.4 nanoseconds, yet my larger reads only seem to get close to the time of a typical read from the L2 cache. I most likely didn't read from the main memory, as I didn't have a run that exceeded 5 nanoseconds per byte.
       **3.** After inspecting my CPU (which is a Intel(R) Core(TM) i5-7267U CPU @ 3.10GHz), my cache size is at 4096 KB. This is larger than what I expected, but this number still aligns with the graph as the read time per byte increased wildly when passing 4096KB. Furthermore, I believe using buffer sizes beyond 2^25 would provide a more accurate depiction of my computer's memory.

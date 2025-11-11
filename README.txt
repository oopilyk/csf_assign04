CONTRIBUTIONS

Kyle Li: implementation
Jacob Peery: experimentation

REPORT

An explanation for the times below is that as the threshhold is decreased and data is divided into smaller chunks, more processes can run concurrently.
The parallelism allows multiple operations across multiple CPU cores, reducing the total real time elapsed.
Decreasing the threshhold from 2097152 bytes to 65536 bytes speeds up the process from 0.389s to .108 seconds. 
The smaller threshhold allows for more balanced workloads among the processes, allowing them to work more in parallel than in sequence.
When the threshhold gets too small, the overhead of creating processes and communicating between them begin to outweigh the benefits, as the threshhold from 65536 of .108s goes up to .127s at a threshhold of 16384 bytes.
It somewhat plateuas when it gets too small, but the user and sys times are increasing steadily, showing that the cpu is doing more work.
The optimal threshhold to maximize the speed through concurrency appears to be 65536 bytes.

Test run with threshold 2097152
real    0m0.389s
user    0m0.372s
sys     0m0.009s

Test run with threshold 1048576
real    0m0.220s
user    0m0.384s
sys     0m0.023s

Test run with threshold 524288
real    0m0.149s
user    0m0.414s
sys     0m0.027s

Test run with threshold 262144
real    0m0.122s
user    0m0.428s
sys     0m0.050s

Test run with threshold 131072
real    0m0.113s
user    0m0.443s
sys     0m0.063s

Test run with threshold 65536
real    0m0.108s
user    0m0.472s
sys     0m0.073s

Test run with threshold 32768
real    0m0.124s
user    0m0.489s
sys     0m0.117s

Test run with threshold 16384
real    0m0.127s
user    0m0.528s
sys     0m0.154s
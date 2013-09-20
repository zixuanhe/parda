Reuse distance is a well established approach to characterizing data cache locality based on the stack histogram model. 
This analysis so far has been restricted to ofﬂine use due to the high cost, often several orders of magnitude larger than the execution time of the analyzed code. Parda is the ﬁrst parallel algorithm to compute accurate reuse distances by analysis of memory address traces. The algorithm uses a tunable parameter that enables faster analysis when the maximum needed reuse distance is limited by a cache size upper bound. 

This program is a Parda implementation on file input. parda omp implementation is mainly in parda_omp.c and parda_omp.h. 

Instructions to run file input Parda. 

A) Setup
Step 0: parda use glib standard linux library. If on ubuntu system just execute following sudo command.
sudo apt-get install glib

Step 1: Download sample trace files from project git web page. 
normal_137979.trace is text file and 
binary_137979.trace is the binary file.
This two files record trace data of 'ls' command. 

Step 2: 
$ cd /path/to/parda
$ make
$ ./parda.x --help to see how to run with different flags and run with sequential algorithm. 

B) Config and compile

C) Execution instructions
1) Sequential execution:
$ ./parda.x --input=normal_137979.trace --lines=137979 > seq.hist 

2) Run parda with OpenMP --enable-omp flag. 
Before running with omp we need to seperate the trace files to threads number. For example if we want to run with 4 threads. 
$ ./parda.x --enable-seperate --input=normal_137979.trace --lines=137979 --threads=4 
We will find 4 seperated trace files. 
4_normal_137979.trace_p0.txt 4_normal_137979.trace_p1.txt 
4_normal_137979.trace_p2.txt 4_normal_137979.trace_p3.txt 
$ ./parda.x --enable-omp --input=normal_137979.trace --lines=137979 --threads=4 > omp.re 

3) Run parda with MPI
mpirun -np 4 ./parda.x --input=normal_137979.trace --lines=137979 --enable-mpi


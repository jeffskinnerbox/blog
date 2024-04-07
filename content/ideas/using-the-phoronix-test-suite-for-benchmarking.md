<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# How to Benchmark / Performance Test Your Linux System
[GeekBench][01], [Sysbench][02], [HARDiNFO][03], [PassMark PerformanceTest][04]
and [Phoronix Test Suite][05] are just some of the benchmarking tools avalable for Linux system.


Sources:
* [How to Benchmark Your Linux System](https://linuxconfig.org/how-to-benchmark-your-linux-system)
* [Benchmarking Linux Systems](https://www.baeldung.com/linux/benchmarking)
* [How to benchmark your Ubuntu Linux servers with the Phoronix Test Suite](https://www.techrepublic.com/article/benchmark-ubuntu-linux-servers-phoronix-test-suite/)
* [How to Benchmark Your System (CPU, File IO, MySQL) with Sysbench](https://www.howtoforge.com/how-to-benchmark-your-system-cpu-file-io-mysql-with-sysbench)
* [Linux benchmark scripts and tools](https://linuxblog.io/linux-benchmark-scripts-tools/)
* [Linux System Testing Tools](https://www.baeldung.com/linux/system-testing-tools)


-----


The Phoronix Test Suite is an open-source, cross-platform automated testing/benchmarking software.
The Phoronix Test Suite is the most comprehensive testing and benchmarking platform available for Linux, Solaris, macOS, Windows, and BSD operating systems. The Phoronix Test Suite allows for carrying out tests in a fully automated manner from test installation to execution and reporting.
The Phoronix Test Suite can be used for simply comparing your computer's performance with your friends and colleagues or can be used within your organization for internal quality assurance purposes, hardware validation, and continuous integration / performance management.

OpenBenchmarking.org provides
* Storage of Phoronix Test Suite benchmark result data (including optional system logs, etc).
* Effective collaboration tools for sharing results and efficiently comparing multiple test results and other analytical features.
* Package management system for making accessible new, updated, and third-party test profiles and test suites to users of the Phoronix Test Suite benchmarking software.

* [GitHub: phoronix-test-suite/phoronix-test-suite](https://github.com/phoronix-test-suite/phoronix-test-suite/)
* [Phoronix Test Suite](https://www.phoronix-test-suite.com/)
* [OpenBenchmarking.org](https://openbenchmarking.org/)



```bash
# to run the benchmark paste/type
sudo curl https://raw.githubusercontent.com/TheRemote/PiBenchmarks/master/Storage.sh | sudo bash

# benchmark suite which allows you to quickly get an impression of system performance
# https://www.howtoforge.com/how-to-benchmark-your-system-cpu-file-io-mysql-with-sysbench
# https://www.phoronix-test-suite.com/

# cpu benchmark
sysbench cpu --cpu-max-prime=20000 --threads=4 --time=0 --events=10000 run

# file io benchmark
sysbench --test=fileio --file-total-size=150G prepare    # create a test file that is much bigger than your RAM (because otherwise, the system will use RAM for caching which tampers with the benchmark results) - 150GB is a good value
.
.
.
```


------


# Sysbench Benchmarking Tool
Sysbench is a simple to use benchmark tool that features tests for CPU, memory, I/O, and even database performance testing.
It’s a command line utility that is part of the Linux distribution repositories.
All the tests are easy to execute and you can do a test run with many options but it simple to use defaults.
For example, to run a CPU test, do `sysbench cpu run` (could have used `fileio`, `cpu`, `memory`, `threads`, or `mutex`)
and to see your options for the CPU test, do `sysbench cpu help`
Change the command `run` to `help` to get the options specific to that test.

Sources:
* [How to Setup Sysbench for CPU and Memory Benchmarking on a Linux Machine](https://webhostinggeeks.com/howto/how-to-setup-sysbench-for-cpu-and-memory-benchmarking-on-a-linux-machine/)
* [Stress Testing in CentOS: Using Sysbench and Stress Commands](https://medium.com/@chachia.mohamed/stress-testing-in-centos-using-sysbench-and-stress-commands-2c4530122c45)
* [Attack CPU, Memory of a Linux machine using Stress and Stress-ng commands](https://gvasanka.medium.com/attack-cpu-memory-of-a-linux-machine-using-stress-and-stress-ng-commands-9a7aa1ee0a25)
* [Testing I/O Performance with Sysbench](https://www.alibabacloud.com/blog/testing-io-performance-with-sysbench_594709)

#### Step 1: Install Sysbench
Let's start by installing Sysbench on your system.

```bash
# install sysbench
sudo apt update
sudo apt install sysbench

# what version of sysbench was installed
$ sysbench --version
sysbench 1.0.20

# print the help message specific for the 'cpu' test
$ sysbench cpu help
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3)

cpu options:
  --cpu-max-prime=N upper limit for primes generator [10000]

# print the help message specific for the 'memory' test
$ sysbench memory help
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3)

memory options:
  --memory-block-size=SIZE    size of memory block for test [1K]
  --memory-total-size=SIZE    total size of data to transfer [100G]
  --memory-scope=STRING       memory access scope {global,local} [global]
  --memory-hugetlb[=on|off]   allocate memory from HugeTLB pool [off]
  --memory-oper=STRING        type of memory operations {read, write, none} [write]
  --memory-access-mode=STRING memory access mode {seq,rnd} [seq]
```

For the the overall help message, do the following:

```bash
# print the full help message
$ sysbench --help
Usage:
  sysbench [options]... [testname] [command]

Commands implemented by most tests: prepare run cleanup help

General options:
  --threads=N                     number of threads to use [1]
  --events=N                      limit for total number of events [0]
  --time=N                        limit for total execution time in seconds [10]
  --forced-shutdown=STRING        number of seconds to wait after the --time limit before forcing shutdown, or 'off' to disable [off]
  --thread-stack-size=SIZE        size of stack per thread [64K]
  --rate=N                        average transactions rate. 0 for unlimited rate [0]
  --report-interval=N             periodically report intermediate statistics with a specified interval in seconds. 0 disables intermediate reports [0]
  --report-checkpoints=[LIST,...] dump full statistics and reset all counters at specified points in time. The argument is a list of comma-separated values representing the amount of time in seconds elapsed from start of test when report checkpoint(s) must be performed. Report checkpoints are off by default. []
  --debug[=on|off]                print more debugging info [off]
  --validate[=on|off]             perform validation checks where possible [off]
  --help[=on|off]                 print help and exit [off]
  --version[=on|off]              print version and exit [off]
  --config-file=FILENAME          File containing command line options
  --tx-rate=N                     deprecated alias for --rate [0]
  --max-requests=N                deprecated alias for --events [0]
  --max-time=N                    deprecated alias for --time [0]
  --num-threads=N                 deprecated alias for --threads [1]

Pseudo-Random Numbers Generator options:
  --rand-type=STRING random numbers distribution {uniform,gaussian,special,pareto} [special]
  --rand-spec-iter=N number of iterations used for numbers generation [12]
  --rand-spec-pct=N  percentage of values to be treated as 'special' (for special distribution) [1]
  --rand-spec-res=N  percentage of 'special' values to use (for special distribution) [75]
  --rand-seed=N      seed for random number generator. When 0, the current time is used as a RNG seed. [0]
  --rand-pareto-h=N  parameter h for pareto distribution [0.2]

Log options:
  --verbosity=N verbosity level {5 - debug, 0 - only critical messages} [3]

  --percentile=N       percentile to calculate in latency statistics (1-100). Use the special value of 0 to disable percentile calculations [95]
  --histogram[=on|off] print latency histogram in report [off]

General database options:

  --db-driver=STRING  specifies database driver to use ('help' to get list of available drivers) [mysql]
  --db-ps-mode=STRING prepared statements usage mode {auto, disable} [auto]
  --db-debug[=on|off] print database-specific debug information [off]


Compiled-in database drivers:
  mysql - MySQL driver
  pgsql - PostgreSQL driver

mysql options:
  --mysql-host=[LIST,...]          MySQL server host [localhost]
  --mysql-port=[LIST,...]          MySQL server port [3306]
  --mysql-socket=[LIST,...]        MySQL socket
  --mysql-user=STRING              MySQL user [sbtest]
  --mysql-password=STRING          MySQL password []
  --mysql-db=STRING                MySQL database name [sbtest]
  --mysql-ssl[=on|off]             use SSL connections, if available in the client library [off]
  --mysql-ssl-cipher=STRING        use specific cipher for SSL connections []
  --mysql-compression[=on|off]     use compression, if available in the client library [off]
  --mysql-debug[=on|off]           trace all client library calls [off]
  --mysql-ignore-errors=[LIST,...] list of errors to ignore, or "all" [1213,1020,1205]
  --mysql-dry-run[=on|off]         Dry run, pretend that all MySQL client API calls are successful without executing them [off]

pgsql options:
  --pgsql-host=STRING     PostgreSQL server host [localhost]
  --pgsql-port=N          PostgreSQL server port [5432]
  --pgsql-user=STRING     PostgreSQL user [sbtest]
  --pgsql-password=STRING PostgreSQL password []
  --pgsql-db=STRING       PostgreSQL database name [sbtest]

Compiled-in tests:
  fileio - File I/O test
  cpu - CPU performance test
  memory - Memory functions speed test
  threads - Threads subsystem performance test
  mutex - Mutex performance test

See 'sysbench <testname> help' for a list of options for each test.
````

#### Step 2: Test Preperation
* reboot system
* 'turn-off' any periodic background processes
* execute test without browser, etc. running.  Just have a terminal open to run the tests.

#### Step 3: Perform CPU Performance Testing
We are looking for the CPU testing to follow these guidelines:

1. CPU Test (Single Thread)
    * **Number of threads:** The test was run with a single thread.
    * **CPU speed:** The more system event the better
    * **Latency:** The average time taken to process an event should a fraction of a milliseconds, and the smaller the better.
    * **Threads fairness:** All events should be evenly distributed among the threads, with no significant deviation.
2. CPU Test (Multi-threaded)
    * **Number of threads:** The test was run with 4 threads.
    * **CPU speed:** With more threads, the system should process nearly 4x improvement from the single-threaded test.
    * **Latency:** The average processing time remains consistent with the single-threaded test.
    * **Threads fairness:** Events should be fairly distributed among the threads, with a minor standard deviation.

```bash
# test the cpu using a single and multiple threads
sysbench cpu run
sysbench cpu --threads=4 run


sysbench cpu run > sysbench-cpu-1-thread
sysbench cpu --threads=4 run > sysbench-cpu-4-thread
```

#### Step 4: Peform Memory Performance Testing
We are looking for the Memory testing to follow these guidelines:

1. Memory Test (Read)
    * **Memory block size:** The size of the memory block being read was 1K.
    * **Memory operations type:** The test focused on read operations.
    * **Total operations:** The more MiB/sec the better.
    * **Latency:** The average time for memory operations should be very low, close to 0 milliseconds.
2. Memory Test (Write)
    * **Memory block size:** The size of the memory block being written was 1K.
    * **Memory operations type:** The test focused on write operations.
    * **Total operations:** The more MiB/sec the better.
    * **Latency:** The average time for memory operations should be very low, close to 0 milliseconds.

```bash
# test the memory read speed using a single and multiple threads
sysbench memory --memory-oper=read run
sysbench memory --memory-oper=read --threads=4 run

# test the memory write speed using a single and multiple threads
sysbench memory --memory-block-size=1K --memory-total-size=10G --memory-oper=write run
sysbench memory --memory-block-size=1K --memory-total-size=10G --memory-oper=write --threads=4 run


sysbench memory --memory-oper=read run > sysbench-read-1-thread
sysbench memory --memory-oper=read --threads=4 run > sysbench-read-4-thread

sysbench memory --memory-block-size=1K --memory-total-size=10G --memory-oper=write run > sysbench-write-1-thread
sysbench memory --memory-block-size=1K --memory-total-size=10G --memory-oper=write --threads=4 run > sysbench-write-4-thread
```

#### Step 5: Peform File I/O Performance Testing

```bash
# test the file i/o speed using a single and multiple threads
sysbench fileio --file-num=128 --file-total-size=2G --file-rw-ratio=1.5 --file-test-mode=seqwr run
sysbench fileio --threads=4 run


sysbench fileio --file-num=128 --file-total-size=2G --file-rw-ratio=1.5 --file-test-mode=seqwr run > sysbench-fileio-1-thread
sysbench fileio --file-num=128 --file-total-size=2G --file-rw-ratio=1.5 --file-test-mode=seqwr --threads=4 run > sysbench-fileio-4-thread
```


------


# Phoronix Test Suite
The Phoronix Test Suite is provided via a `.deb` Debien package.
The Debien packages are third-party tools used to install software packages in Linux distributions.
When we use the install tool for Debien package,
there is a possibility that all of the respective dependencies may not install.

Sources:
* [How to Benchmark Your Linux System](https://linuxconfig.org/how-to-benchmark-your-linux-system)

#### Step 1: Install Phoronix
To do the install,
log into your Ubuntu Server instance and download the **latest** Phoronix Test Suite `.deb` file.
You should find that file at `https://github.com/phoronix-test-suite/phoronix-test-suite/releases`:

```bash
# dowenload the phoronix test suite .deb file
cd ~/Downloads
wget https://github.com/phoronix-test-suite/phoronix-test-suite/releases/download/v10.8.4/phoronix-test-suite_10.8.4_all.deb

# install the tool with
sudo dpkg -i phoronix*.deb

# the installation may error out because there are still dependencies to meet
# you can fix that error and complete the installation with the single command
sudo apt-get install -f

# you can verify the installation with
phoronix-test-suite
```

The above verification step should list out all of the help information for the command.

#### Step 2: John The Ripper Benchmark
John The Ripper is a classic password cracking program used by security testers,
but the stress that it places on your CPU makes it an ideal program to test with.
The test will run three times, and you’ll see your results displayed in the terminal.

```bash
# install 'john the ripper'
phoronix-test-suite install john-the-ripper

# run the 'john the ripper' test
phoronix-test-suite run john-the-ripper
```

#### Step 3: LuxMark
LuxMark is another performance test that measures both OpenCL performance of both the CPU and GPU.

```bash
phoronx-test-suite install luxmark
phoronix-test-suite run luxmark
```

#### Step 4: Compile Firefox
Firefox codebase is massive, and it takes a lot of time and system resources to compile.
Its a real world test, especially for your CPU, try compiling Firefox.

```bash
phoronix-test-suite install compile-firefox
phoronix-test-suite run compile-firefox
```



[01]:https://www.geekbench.com/
[02]:https://manpages.ubuntu.com/manpages/trusty/man1/sysbench.1.html
[03]:https://www.usro.net/products/hardinfo/
[04]:https://www.passmark.com/products/pt_linux/index.php
[05]:https://www.phoronix-test-suite.com/
[06]:
[07]:
[08]:
[09]:
[10]:


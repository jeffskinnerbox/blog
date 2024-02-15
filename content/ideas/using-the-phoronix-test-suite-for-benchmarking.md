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

# Install the Phoronix Test Suite
The Phoronix Test Suite is provied via a `.deb` Debien package.
The Debien packages are third-party tools used to install software packages in Linux distributions.
When we use the install tool for Debien package,
there is a possibility that all of the respective dependencies may not install.

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


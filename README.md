Current Version: 2.5.0 (Jun 22, 2017) - Changelog
Source tarball: https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0.tar.gz

Binaries for Windows:

https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0-win32.zip (32-bit)
https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0-win64.zip (64-bit)

Binaries for Linux:

https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0-linux-x86.tar.gz (x86)
https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0-linux-x86_64.tar.gz (x86-64)

Binaries for Mac OS X:

https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0-osx32.zip (32-bit)
https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0-osx64.zip (64-bit)

SHA-256 Checksums
Code:

ea16761a952b8f0fbba22fd16d48bb5e20abc48a10af99a00c70c332b3cb54f5  pooler-cpuminer-2.5.0.tar.gz
c385a7a73730b40548c5c658aa476dd4a95d4629d1c159a1ef830a0068c1c744  pooler-cpuminer-2.5.0-linux-x86.tar.gz
bf390ab6b801536aca3f8ece535ee71550afdc984ea5de67195b15ff3c248539  pooler-cpuminer-2.5.0-linux-x86_64.tar.gz
b45c7838aec8f704ef6700d5feb27f8e6c798bb0a42ce847bf3b203188d4183e  pooler-cpuminer-2.5.0-osx32.zip
c86ba412b3c10163f4623272e5ff746c57373ef403251472ef41a9a84ce33332  pooler-cpuminer-2.5.0-osx64.zip
dfa8713404b709f84550dda1af642ca49af72a4ec0e333eb9c3f797ae2554e2e  pooler-cpuminer-2.5.0-win32.zip
4cf4af2ae1d1a42c97b88ca91cfa1b49851efecbb62d6fafe0a5152ffd47fde1  pooler-cpuminer-2.5.0-win64.zip

Basic usage examples

Code:

$ ./minerd --url=http://myminingpool.com:9332 --userpass=my.worker:password

$ ./minerd --url=stratum+tcp://myminingpool.com:3333 --userpass=my.worker:password

For more information:

Code:

$ ./minerd --help

Building instructions
Installing dependencies for building on Debian, Ubuntu and other APT-based distros:

Code:

$ sudo apt-get install make libcurl4-openssl-dev
Installing dependencies for building on Fedora, RHEL, CentOS and other yum-based distros:

Code:

$ sudo yum install gcc make curl-devel
Installing dependencies for building on OpenSUSE and other ZYpp-based distros:

Code:

$ sudo zypper in gcc make libcurl-devel
Recipe for building on Linux:

Code:

$ wget https://github.com/pooler/cpuminer/releases/download/v2.5.0/pooler-cpuminer-2.5.0.tar.gz

$ tar xzf pooler-cpuminer-*.tar.gz

$ cd cpuminer-*

$ ./configure CFLAGS="-O3"

$ make


FAQ / Troubleshooting

Q: Should I call this miner "cpuminer" or "minerd"?

A: The software package is called "cpuminer". "minerd" ("miner daemon") is just the name of the executable file provided by the package.

Q: My antivirus flags the Windows binary as malware.

A: That's a known false positive. More information here.

Q: When I click on minerd.exe a black window flashes up and then disappears.

A: This is a command-line application, it has no graphical interface. You'll need to learn how to use the command line interface (CLI) of your operating system first.

Q: Can I mine (insert your cryptocoin here) with this miner?

A: Only if its proof-of-work algorithm is scrypt or SHA-256d. This miner does not currently support other algorithms such as Keccak, scrypt-jane, X11, etc. Forks of this project may provide additional algorithms, but I do not maintain them and they are not discussed here, so if you have questions about them please contact their authors.

Q: When running configure I get the error "C compiler cannot create executables".

A: Make sure you typed CFLAGS="-O3" with a big O, not with a zero.

Q: autogen.sh dies with "error: possibly undefined macro: AC_MSG_ERROR".
Q: configure chokes on something like "LIBCURL_CHECK_CONFIG(, 7.15.2, ,'".

A: Make sure you have installed the development package for libcurl. If you have and you're still getting the error when compiling from git, try compiling from tarball instead.

Q: I'm trying to connect to a Stratum server, but I get "HTTP request failed: Empty reply from server".

A: Make sure you specified the correct protocol in the server URL (stratum+tcp://).

Q: Is there any command-line option I can play with to make it mine faster?

A: No. The miner automatically picks the best settings for the CPU it is run on.

Q: What's the difference between the two algorithms, scrypt and sha256d?

A: They are completely different proof-of-work algorithms. You must use scrypt for Litecoin, and you must use sha256d for Bitcoin. The default algorithm is scrypt, so for Bitcoin mining you have to specify --algo=sha256d.

Q: Will this miner use a lot of RAM when using the scrypt algorithm?

A: No, that's a GPU thing.

Q: How do I make the miner write its output to a file instead of printing it to the screen?

A: Just redirect the standard error stream to file:
Code:

minerd [OPTIONS] 2> myfile

You may also want to use the --quiet/-q option to disable the per-thread hashmeter.
On *nix, you probably also want to use the --background/-B option to fork in the background.

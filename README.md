

# cacao : Compute And Control for Adaptive Optics


<img align="left" src="cacao-logo-250pix.png">

cacao is a computation engine for adaptive optics control.

**Compute Performance**: Uses multi-core CPUs and GPGPUs for [high computing throughput](https://github.com/cacao-org/cacao/wiki/Compute-Performance-Benchmarks). Written in C, optimized for performance. Holds images in RAM, with image stream support (shared memory with low-latency IPC support). cacao uses [milk](https://github.com/milk-org/milk). 


**User input**: Executable launches a [command line interface (CLI)](https://cacao-org.github.io/cacao/page_userinput.html) from which functions are accessible. Type "help" in the CLI to get started.


**Modular**, [easy to add functions](https://cacao-org.github.io/cacao/page_LoadingModules.html), loaded at runtime as shared objects.



---


## Getting help, Documentation

Topic                        |  Chat room                             |  Documentation             | 
-----------------------------|----------------------------------------|--------------------|
How to use cacao ?           | [![Gitter](https://badges.gitter.im/cacao-org/community.svg)](https://gitter.im/cacao-org/community)  Community | [Online documentation]( http://CACAO-org.github.io/cacao/index.html )  |
Configuring computer system  | [![Gitter](https://badges.gitter.im/cacao-org/RTCconfig.svg)](https://gitter.im/cacao-org/RTCconfig)  Hardware / OS setup | [RTC setup]( https://github.com/cacao-org/cacao/wiki/Seeting-up-a-RTC-system ) |
Software development         | [![Gitter](https://badges.gitter.im/cacao-org/codedev.svg)](https://gitter.im/cacao-org/codedev)      Developers | [coding standards]( http://CACAO-org.github.io/cacao/page_coding_standards.html ) and  [Online documentation]( http://CACAO-org.github.io/cacao/index.html )|



Report bugs and issues on [this page]( https://github.com/cacao-org/cacao/issues ) and discuss them on the [Developers chat](https://gitter.im/cacao-org/codedev).



---

## Installing cacao


### Source code status

[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/8fc93c97bde340078b02340e71b10580)](https://www.codacy.com/app/oguyon/CACAO?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=CACAO-org/CACAO&amp;utm_campaign=Badge_Grade)


|     branch       |   version             |  status                     | latest        |
|------------------|-----------------------|-----------------------------|---------------|
**master** | [![latesttag](https://img.shields.io/github/tag/cacao-org/cacao.svg)](https://github.com/cacao-org/cacao/tree/master) | [![Build Status](https://travis-ci.org/cacao-org/cacao.svg?branch=master)](https://travis-ci.org/cacao-org/cacao) | ![lastcommit](https://img.shields.io/github/last-commit/cacao-org/cacao/master.svg)
[**dev**](https://github.com/cacao-org/cacao/tree/dev) | | [![Build Status dev](https://travis-ci.org/cacao-org/cacao.svg?branch=dev)](https://travis-ci.org/cacao-org/cacao) | ![lastcommit](https://img.shields.io/github/last-commit/cacao-org/cacao/dev.svg)



### Install steps

```bash
git clone --recursive https://github.com/cacao-org/cacao cacao
cd cacao
mkdir _build
cd _build
cmake ..
# If you use NVIDIA GPUs, install cuda and magma libraries, and use "cmake .. -DUSE_MAGMA=ON"
make
sudo make install
```


### Post-installation 

You may need to add /usr/local/lib to LD_LIBRARY_PATH environment variable:
```bash
echo "/usr/local/lib" > usrlocal.conf
sudo mv usrlocal.conf /etc/ld.so.conf.d/
sudo ldconfig -v
```

Unless you have a separate install of milk on your system, a symbolic link to milk is required for milk scripts that are included in cacao:

```bash
sudo ln -s /usr/local/bin/cacao /usr/local/bin/milk
```

Add milk executable scripts to PATH environment variable. Add this line to the .bashrc file (change source code location as needed):
```bash
export PATH=$PATH:/home/myname/src/cacao/src/CommandLineInterface/scripts
```


---


## Getting Started

All functions are accessible from the command line interface (CLI). Enter the CLI and type "help" for instructions.

```bash
cacao
```



---

## Tools

Both cacao and milk use a common shared memory data stream format. See [ImageStreamIO module](https://github.com/milk-org/ImageStreamIO) for details.

### Viewing real-time data streams

Additional software is required to view real-time data streams. Several options exist:

  * [shmimviewGTK](https://github.com/milk-org/shmimviewGTK), a lightweight efficient GTK-based viewer.
  * [milk2ds9](https://github.com/jaredmales/milk2ds9) uses ds9 to view data streams (convenient for ds9 users)
  * [rtimv](https://github.com/jaredmales/rtimv), a qt-based image viewer, higher performance than ds9 option
  * [shmimviewqt](https://github.com/milk-org/shmimviewqt), another qt-based option (less polished than rtimv)
  * [xaosim](https://github.com/fmartinache/xaosim)'s shmview image viewer, using python qt interface
  
### Python interface to data streams

Python users can read/write milk/cacao's data streams using additional packages:

  * [pyImageStreamIO](https://github.com/milk-org/pyImageStreamIO) provides an interface to data streams.
  * [xaosim](https://github.com/fmartinache/xaosim) includes a python interface to data streams.. and much more



---



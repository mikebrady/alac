ALAC
====

This repository is a clone of the Apple Lossless Audio Codec (ALAC) repository at http://alac.macosforge.org with added files to enable it to be built using GNU `autotools`. Use it to build and install the ALAC library `libalac`.

The added files are based on work done by [Tiancheng "Timothy" Gu](https://github.com/TimothyGu)  in his repository https://github.com/TimothyGu/alac with some changes. Many thanks to him for his work. This respository is bare-bones – for Visual Studio or Debian packaging support or for `man` pages, please go to Timothy's repository.

**Note:** In the rest of the note, a command prefixed with `#` means that it must be executed in superuser mode. The `$` prefix means it should be executed in regular user mode.

Install Build Tools
---
Building `libalac` requires a number of tools, such a the compiler and linker, `git` and more. Ensure they are already in place by running the following command. If the tools are already in place, it'll do no harm. 
```
# apt get update
# apt-get install build-essential git autoconf automake libtool
```
Download, Build, Install
---

To download, build and install `libalac` do the following:

* Clone the repository and `cd` into the folder:
```
$ git clone https://github.com/mikebrady/alac.git
$ cd alac
```
* Configure the build and make the library:
```
$ autoreconf -fi
$ ./configure
$ make
```
The `autoconfigure` command may take a long time. You may get a warning which you can ignore:
```
aclocal: warning: couldn't open directory 'm4': No such file or directory
```

* Install the library:
```
# make install
```
Make it Available
---
To make the library visible during compilation, you need to tell `ld` about it. Be careful here – if you are on FreeBSD, the Linux command will mess up your system. On Linux only, use the following command:
```
# ldconfig
```

Using the library
---

The library can be found and linked to via `pkg-config` – the module name is `alac`.

Thus:
```
PKG_CHECK_MODULES([ALAC], [alac], [LIBS="${ALAC_LIBS} ${LIBS}"])
```
should work in a `configure.ac` file. If you are using `AC_CHECK_LIB`, something like this will work:
```
AC_CHECK_LIB([alac], [BitBufferInit], , AC_MSG_ERROR(Apple ALAC Decoder support requires the alac library!))
```

On FreeBSD you must add the location of the `alac.pc` file to the `PKG_CONFIG_PATH`, if it exists, and define it otherwise. Here is what you do if it doesn't already exist:
```
$ PKG_CONFIG_PATH="/usr/local/lib/pkgconfig"
$ export PKG_CONFIG_PATH
```

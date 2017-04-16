ALAC
====

This repository is a clone of the Apple Lossless Audio Codec (ALAC) repository at http://alac.macosforge.org with added files to enable it to be built using GNU `autotools`. Use it to build and install the ALAC library `libalac`.

The added files are based on work done by [Tiancheng "Timothy" Gu](https://github.com/TimothyGu)  in his repository https://github.com/TimothyGu/alac with some changes. Many thanks to him for his work. This respository is bare-bones – for Visual Studio or Debian packaging support or for `man` pages, please go to Timothy's repository.

###Download, build, install

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
* Finally, to make the library visible during compilation, you need to tell `ld` about it. Be careful here – if you are on FreeBSD, the Linux commands will mess up your system. On Linux, use the following command:
```
# ldconfig -v
```
On FreeBSD you must add the location of the `soxr.pc` file to the `PKG_CONFIG_PATH`, if it exists, and define it otherwise. Here is what you do if it doesn't already exist:
```
$ PKG_CONFIG_PATH="/usr/local/lib/pkgconfig"
$ export PKG_CONFIG_PATH
```
That's it – the library can now be linked to via `pkg-config`: the module name is `alac`, thus:
```
PKG_CHECK_MODULES([ALAC], [alac], [LIBS="${ALAC_LIBS} ${LIBS}"])
```
should work. If you are using `AC_CHECK_LIB`, something like this will work:
```
AC_CHECK_LIB([alac], [BitBufferInit], , AC_MSG_ERROR(Apple ALAC Decoder support requires the alac library!))
```

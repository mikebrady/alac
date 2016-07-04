ALAC
====

This repository is a clone of the Apple Lossless Audio Codec at http://alac.macosforge.org with added files to enable it to be built using GNU `autotools`. Use it to build and install the Apple Lossless Audio Codec (ALAC) library `libalac`.

The added files are based on work done by Tiancheng "Timothy" Gu – @TimothyGu – in his repository https://github.com/TimothyGu/alac/ with some changes. Many thanks to him for his work. This respository is bare-bones – it does not cater for Visual Studio nor does it deal with Debian packaging. Similarly, it does not install `man` pages.

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
* Install the library:
```
$ sudo make install
```
* Finally, to make the library visible during compilation, you need to tell `ld` to catalogue it:
```
$ sudo ldconfig -v
```
That's it. 

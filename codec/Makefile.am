## Copyright (c) 2013 Tiancheng "Timothy" Gu
## Modifications copyright (c) 2016 Mike Brady
## Licensed under the Apache License, Version 2.0 (the "License");
## you may not use this file except in compliance with the License.
## You may obtain a copy of the License at
## 
##     http://www.apache.org/licenses/LICENSE-2.0
## 
## Unless required by applicable law or agreed to in writing, software
## distributed under the License is distributed on an "AS IS" BASIS,
## WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
## See the License for the specific language governing permissions and
## limitations under the License.

lib_LTLIBRARIES = libalac.la

libalac_la_CPPFLAGS = -Wno-multichar
libalac_la_LDFLAGS = -version-info @ALAC_VERSION@

libalac_la_SOURCES = \
    EndianPortable.c \
    ALACBitUtilities.c \
    ALACDecoder.cpp \
    ALACEncoder.cpp \
    ag_dec.c \
    ag_enc.c \
    dp_dec.c \
    dp_enc.c \
    matrix_dec.c \
    matrix_enc.c

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = alac.pc

# Install to include/alac
alacincludedir = $(includedir)/alac

# Install everything
alacinclude_HEADERS = *.h

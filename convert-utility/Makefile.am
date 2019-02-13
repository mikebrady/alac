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

bin_PROGRAMS = alacconvert$(EXEEXT)

alacconvert_CPPFLAGS = -Wno-multichar -I../codec
alacconvert_LDADD = ../codec/libalac.la
alacconvert_SOURCES = \
    main.cpp \
    CAFFileALAC.cpp

noinst_HEADERS = $(top_srcdir)/convert-utility/CAFFileALAC.h

dnl                                               -*- Autoconf -*-
dnl Process this file with autoconf to produce a configure script.

dnl Copyright (c) 2013 Tiancheng "Timothy" Gu
dnl Modifications copyright (c) 2016 Mike Brady
dnl Licensed under the Apache License, Version 2.0 (the "License");
dnl you may not use this file except in compliance with the License.
dnl You may obtain a copy of the License at
dnl 
dnl     http://www.apache.org/licenses/LICENSE-2.0
dnl 
dnl Unless required by applicable law or agreed to in writing, software
dnl distributed under the License is distributed on an "AS IS" BASIS,
dnl WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
dnl See the License for the specific language governing permissions and
dnl limitations under the License.

AC_PREREQ([2.68])
AC_INIT([alac], [0.0.7], [mikebrady@eircom.net])
AM_INIT_AUTOMAKE
AC_CONFIG_SRCDIR([codec/dp_enc.c])
AC_CONFIG_HEADERS([config.h])

dnl AC_CONFIG_AUX_DIR(.)
AC_CONFIG_MACRO_DIR([m4])
dnl AM_INIT_AUTOMAKE([tar-ustar foreign])
dnl m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])
dnl AM_MAINTAINER_MODE

dnl Various options for configure
AC_ARG_ENABLE([example],
            [AS_HELP_STRING([--enable-example],
                [enable example encoding program (default is no)])],
            [example=$enableval], [example=no])

dnl Automake conditionals to set
AM_CONDITIONAL(EXAMPLE, test x$example = xyes)

dnl Checks for programs.
AC_PROG_CC
AC_PROG_CXX

dnl Checks for header files.
AC_CHECK_HEADERS([stdint.h stdlib.h string.h])

dnl Checks for typedefs, structures, and compiler characteristics.
dnl AC_CHECK_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_INT8_T
AC_TYPE_SIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_CHECK_FUNCS([memset strrchr])

dnl Setup for libtool
LT_INIT

dnl soname version to use
dnl goes by ‘current[:revision[:age]]’ with the soname ending up as
dnl current.age.revision.
ALAC_VERSION=0

AC_SUBST(ALAC_VERSION)

AC_CONFIG_FILES([Makefile
                 codec/Makefile
                 convert-utility/Makefile
                 codec/alac.pc])
AC_OUTPUT

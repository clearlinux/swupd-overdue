#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([swupd-overdue], 1[], [dev@lists.clearlinux.org])
AM_INIT_AUTOMAKE([foreign -Wall -W subdir-objects])
AM_SILENT_RULES([yes])

AC_CONFIG_SRCDIR([swupd-overdue.c])
AC_CONFIG_HEADERS([config.h])

AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_MAKE_SET

AC_CHECK_HEADERS([stdlib.h string.h unistd.h])
AC_CHECK_FUNCS([memset])

PKG_CHECK_MODULES([SYSTEMD], [systemd])

dir=""
AC_ARG_WITH([systemdsystemunitdir], AS_HELP_STRING([--with-systemdsystemunitdir=DIR],
            [path to systemd system service dir @<:@default=/usr/lib/systemd/system@:>@]), [dir=${withval}],
            [dir="$($PKG_CONFIG --variable=systemdsystemunitdir systemd)"])
test -z "${dir}" && dir=/usr/lib/systemd/system
AC_SUBST(systemdsystemunitdir, [${dir}])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

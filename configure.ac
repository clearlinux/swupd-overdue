#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([swupd-overdue], [6], [dev@lists.clearlinux.org])
AM_INIT_AUTOMAKE([foreign -Wall -W subdir-objects no-dist-gzip dist-xz])
AM_SILENT_RULES([yes])

AC_CONFIG_SRCDIR([swupd-overdue.c])
AC_CONFIG_HEADERS([config.h])

AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_MAKE_SET

AC_CHECK_HEADERS([netdb.h stdlib.h string.h unistd.h systemd/sd-bus.h time.h errno.h limits.h])
AC_CHECK_FUNCS([memset])
AC_CHECK_FUNCS([sleep])
AC_CHECK_FUNCS([gethostbyname])
AC_CHECK_FUNCS([strtol])

PKG_CHECK_MODULES([SYSTEMD], [systemd])
PKG_CHECK_MODULES([LIBSYSTEMD], [libsystemd], [],
            [AC_MSG_ERROR([*** libsystemd library not found])])

dir=""
AC_ARG_WITH([systemdsystemunitdir], AS_HELP_STRING([--with-systemdsystemunitdir=DIR],
            [path to systemd system service dir @<:@default=/usr/lib/systemd/system@:>@]), [dir=${withval}],
            [dir="$($PKG_CONFIG --variable=systemdsystemunitdir systemd)"])
test -z "${dir}" && dir=/usr/lib/systemd/system
AC_SUBST(systemdsystemunitdir, [${dir}])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

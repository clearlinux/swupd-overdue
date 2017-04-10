AM_CFLAGS = \
	-fstack-protector -Wall -pedantic \
	-Wstrict-prototypes -Wundef -fno-common \
	-Werror-implicit-function-declaration \
	-Wformat -Wformat-security -Werror=format-security \
	-Wno-conversion -Wunused-variable -Wunreachable-code \
	-Wall -W -D_FORTIFY_SOURCE=2 -std=c11

bin_PROGRAMS = \
	swupd-overdue

swupd_overdue_SOURCES = \
	swupd-overdue.c

swupd_overdue_CFLAGS = \
	$(LIBSYSTEMD_CFLAGS)

swupd_overdue_LDADD = \
	$(LIBSYSTEMD_LIBS)

EXTRA_DIST = \
	COPYING \
	swupd-overdue.md \
	swupd-overdue.service

dist_man_MANS = \
	swupd-overdue.1

DISTCHECK_CONFIGURE_FLAGS = \
	--with-systemdsystemunitdir=$$dc_install_base/$(systemdsystemunitdir) \
	--with-systemdtmpfilesdir=$$dc_install_base/$(tmpfilesdir)

systemdsystemunit_DATA = \
	swupd-overdue.service

swupd-overdue.1: swupd-overdue.md
	ronn swupd-overdue.md
	rm -f swupd-overdue.1.html

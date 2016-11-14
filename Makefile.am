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

EXTRA_DIST = \
	COPYING \
	swupd-overdue.service

DISTCHECK_CONFIGURE_FLAGS = \
	--with-systemdsystemunitdir=$$dc_install_base/$(systemdsystemunitdir) \
	--with-systemdtmpfilesdir=$$dc_install_base/$(tmpfilesdir)

systemdsystemunit_DATA = \
	swupd-overdue.service

swupd-overdue(1) -- Trigger OS updates if exceeding a time threshold
====================================================================

## SYNOPSIS

`swupd-overdue [threshold]`

## DESCRIPTION

This program checks that OS updates are applied at boot time if
there is an indication that OS updates have not been applied
for a specified (threshold) time (in seconds).

The update is started by signalling `systemd` that the
`swupd-update.service` should be started, using `systemctl`. This
requires that this program is executed with appropriate (`root`)
permissions in order to succeed.

The `threshold` defaults to 14 days, and is checked against the
version time stamp file in `/usr/share/clear/versionstamp`. If
the OS has not been updated longer than the `threshold` value,
the OS software update service unit will be started.

The `threshold` value is in seconds. It can be passed optionally
at the command line as argument 1.

If the `swupd-update.service` unit is masked, the update will
fail. If the `swupd-update.timer` unit is masked, but the
`swupd-update.service` is not masked, the update will be
performed.

## SYNTAX

`swupd-overdue` is not meant to be directly executed from the
command line. The system administrator should `systemctl enable
swupd-overdue.service` to ensure that the program is run at
every boot. Additionally, one should ensure that OS software
updates are automatically applied by enabling `swupd-update.timer`
as well.

## EXIT STATUS

On success, 0 is returned, a non-zero failure code otherwise.

## COPYRIGHT

 * Copyright (C) 2016 Intel Corporation, License: CC-BY-SA-3.0

## SEE ALSO

 * swupd(1)

 * https://clearlinux.org/documentation/

## NOTES

Creative Commons Attribution-ShareAlike 3.0 Unported

 * http://creativecommons.org/licenses/by-sa/3.0/

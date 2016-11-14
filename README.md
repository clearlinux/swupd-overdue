## About

This program is meant to be executed as a oneshot daemon at boot
time. It checks to see that the system is running an OS version
that isn't more than 14 days old, and forces an auto-update (through
systemd) if so.

By default, Clear Linux OS performs auto software updates several
times a day, if available. However, these updates are not applied at
boot time. Doing updates at every boot would potentially cause issues
for machines that are in a large cluster, so we want to avoid forcing
an update if the chances are high that it might coalesce with many
machines performing an update.

We also want to avoid updating containers that start and shut down
frequently and do not run for very long periods. Because the default
auto update timer will likely never expire in such a use case, we
need to assure that the image doesn't go on being used without an OS
software update for prolonged periods.

## Notes

The `swupd-overdue.1` manual page is generated using `ronn`. To
re-create it, run `make swupd-overdue.1`. If you want to edit the man
page, make sure to edit `swupd-overdue.md` and not the nroff output
file. The HTML version is discarded.

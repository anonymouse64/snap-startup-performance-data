# Snap Startup Performance Data

This is a repository for the raw data and graphs generated for snap startup investigations.

All of this data was gathered by the [`etrace`](https://github.com/anonymouse64/etrace) program I purpose-built for these investigations.

The following snap revisions were used for gathering this data:

* chromium -> revision 937 (snap version `78.0.3904.97`)
* libreoffice -> revision 162 (snap version `6.3.4.2`)
* mari0 -> revision 6 (snap version `1.6.2+pkg-7fd3`)
* test-snapd-glxgears -> revision 2 (snap version `16`)
* supertuxkart -> revision 229 (snap version `1.0`)
* gnome-calculator -> revision 544 (snap version `3.34.1+git1.d34dc842`)

The data directories here represent data gathered for the following situations:

## data-testrun-exec-bootchart

This was a basic launch of the applications, including all execve syscalls to build a "bootchart" of the executables run during startup.


## data-testrun-ld-cache-exec-bootchart

This was a launch of the applciations, modified to use a snap-private ld.so.cache and not LD_LIBRARY_PATH, with all execve syscalls to show what is specifically faster when we don't use LD_LIBRARY_PATH for dynamic library resolution

## data-testrun-ld-cache-notrace-startup

This was a launch of the applications, modified applications to use a snap-private ld.so.cache, but without any execve syscalls just for measuring launch time.

## data-testrun-notrace-startup

This was a basic launch of the application, without any execve syscalls just for measuring launch time.

## data-testrun-second-exec-bootchart

This was a basic launch of the application, including all execve syscalls, but without $SNAP_USER_DATA deletion after the first run to measure "hot cache" launch times. Note that we still free VM caches, and discard the snap's mount namespace before running again, so this is really just measuring the caching of the snap application.

## data-testrun-second-notrace-startup

This was a basic launch of the application, without any execve syscalls just for measuring launch time, but without $SNAP_USER_DATA deletion after the first run to measure "hot cache" launch times. Note that we still free VM caches, and discard the snap's mount namespace before running again, so this is just measuring caching of the snap application.


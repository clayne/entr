**WARNING:** This is a (possibly outdated and/or unmaintained) fork of https://github.com/eradman/entr . If you want to install entr, go to the [the original repository](https://github.com/eradman/entr) to get the latest release. Likewise, to file an issue or a pull request, head over to the [the original repository](https://github.com/eradman/entr).

Event Notify Test Runner
========================

A utility for running arbitrary commands when files change. Uses [kqueue(2)] or
[inotify(7)] to avoid polling.  `entr` was written to make rapid feedback and
automated testing natural and completely ordinary.

Source Installation - BSD, Mac OS, and Linux
--------------------------------------------

    ./configure
    make test
    make install

To see available build options run `./configure -h`

Docker and Windows Subsystem for Linux
--------------------------------------

To enable a workaround for incomplete inotify support on WSL or Docker for Mac,
set the environment variable `ENTR_INOTIFY_WORKAROUND`.

Man Page Examples
-----------------

Rebuild a project if source files change, limiting output to the first 20 lines:

    $ find src/ | entr sh -c 'make | head -n 20'

Launch and auto-reload a node.js server:

    $ find *.js | entr -r node app.js

Clear the screen and run a query after the SQL script is updated:

    $ echo my.sql | entr -p psql -f /_

Rebuild project if a source file is modified or added to the src/ directory:

    $ while true; do find src/*.rb | entr -d make; done

Self-terminate after a file is updated

    $ find * | entr -p 'kill $PPID'

News
----

A release history as well as features in the upcoming release are covered in the
[NEWS] file.

[kqueue(2)]: http://man.openbsd.org/kqueue.2
[inotify(7)]: http://man.he.net/?section=all&topic=inotify
[NEWS]: https://raw.githubusercontent.com/eradman/entr/master/NEWS

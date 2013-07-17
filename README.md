
Some simple scripts that are intended to run from cron. They create a simple web page
and/or email summarizing the commits that have occurred since the last time the script
was executed. This allows a daily summary of a repository to be mailed round and is
useful given that, for example, git triggers issue alerts each time someone pushes
to the repository.

There is a script for `git` and a script for `svn`. The `git` script just sends round an
email summary (repository browsers are so good a web page is not needed). The `svn` script
creates a web page and an email.

Note that for the moment the configuration options are hard-coded into each script in
`%SETTINGS`. These settings could easily be shifted to a config file.

The scripts create a small file in a directory indicating the most recent SHA1 or subversion
revision so that it will know where to restart.

The crontab entry simply needs to indicate which repository from the settings configuration
hash should be used for this run.

    30 17 * * * /usr/bin/perl /path/bin/summarize-commits-svn -repos svnsoftware
    00 23 * * * /usr/bin/perl /path/bin/summarize-commits-git -rep gitsoftware

The `svn` implementation is based on work Norman Gray did for Starlink. They are here in case
anyone else finds them useful.

The scripts are distributed using GPL v2.

Author: Tim Jenness
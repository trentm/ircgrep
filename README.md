`ircgrep` is a command-line tool for grepping through IRC channel logs

This project lives here: <http://github.com/trentm/ircgrep>


## Installation

Clone the repo and add the "bin" dir to your PATH:

    git clone git@github.com:trentm/ircgrep.git
    export PATH=`pwd`/ircgrep/bin

Alternatively your could add an alias to your ".bashrc" or equivalent:

    alias ircgrep='.../ircgrep/bin/ircgrep'


## Usage

    ircgrep [OPTIONS] CHANNEL PATTERN

Where `CHANNEL` is a known channel with logs and `PATTERN` is a Python regular expression. Use `ircgrep --help` to see all options.


## Examples

Search the node.js logs for occurences of "require.paths":

    ircgrep node.js 'require\.paths'

By default `ircgrep` search back 7 days. You can specify a particular number of days with the `-d|--days N` option:

    ircgrep -d 30 node.js 'require\.main'


## Known channel logs

To grep logs for a channel, ircgrep has to know about a log location for that channel.  For example "#node.js" on irc.freenode.net has backups at <http://nodejs.debuggable.com/>.  Use the following to list known channels:

    ircgrep -l

Is there a channel with publicly available daily logs that you'd like me to add? Please [create an issue](https://github.com/trentm/ircgrep/issues) and lets discuss.


## Why is it slow the first time?

`ircgrep` works by downloading the daily log files to a cache location, parsing them to prepare for searching, and then searching the local files. As a result the first search for a particular day might be slow. Subsequent searches should be fast.

If you are offline you can search already downloaded log files (i.e. skip the update of the local cache) with the `-o|--offline` option.


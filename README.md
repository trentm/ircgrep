`ircgrep` is a command-line tool for grepping through IRC channel logs

This project lives here: <http://github.com/trentm/ircgrep>

## Installation

To install in your Python's global site-packages use one of the following:

    pip install ircgrep
    pypm install ircgrep   # if you use ActivePython (http://www.activestate.com/activepython)


## Known channel logs

To grep logs for a channel, ircgrep has to know about a log location for that channel.  For example "#node.js" on irc.freenode.net has backups at <http://nodejs.debuggable.com/>.  Use the following to list known channels:

    ircgrep -l


## Usage

    ircgrep [OPTIONS] CHANNEL PATTERN

Where `CHANNEL` is a known channel with logs and `PATTERN` is a Python regular expression. Use `ircgrep --help` to see all options.


## Examples

Search the node.js logs for occurences of "require.paths":

    ircgrep node.js 'require\.paths'

By default `ircgrep` search back 7 days. You can specify a particular number of days with the `-d|--days N` option:

    ircgrep -d 30 node.js 'require\.main'


## Why is it slow the first time?

`ircgrep` works by downloading the daily log files to a cache location, parsing them to prepare for searching, and then searching the local files. As a result the first search for a particular day might be slow. Subsequent searches should be fast.

If you are offline you can search already downloaded log files (i.e. skip the update of the local cache) with the `-o|--offline` option.

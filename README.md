## lnav overview
[http://lnav.org](lnav) is a powerful log file reader, designed to take
multiple log files and order them by date.  It understands log file formats
using regular expresions and can highlight sections of line, find errors
and warnings, and more.

### Installation
lnav can be installed via homebrew ([formula](https://formulae.brew.sh/formula/lnav))
```sh
brew install lnav
```
For alternative options refer to the [docs](https://docs.lnav.org/en/latest/intro.html#installation).
## Log format description files for lnav

This repository is a fork of [lnav-formats](https://github.com/PaulWay/lnav-formats) with the following additional lnav formats useful for Splash:
* [monolog](monolog.json)
* [splash_structured_log](splash_structured_log.json) - Cake log format for structured logs
* (Deprecated) [splash_log](splash_log.json) - Cake log format prior to move to structured logs

To install these lnav formats run the following command:
```sh
lnav -i splash_structured_log.json monolog.json
```
# lnav version

Some of these formats use features that are only available in lnav version
0.8.0 or above.  If you get warnings, try renaming the offending files to
.json-unused to see if this fixes things.

# Easy creation of formats

I now provide a new tool, `make_format.pl`, which takes a series of lines from
stdin and turns them into sample lines in a new format.  This can, for
instance, be used by marking several significant lines in lnav and issuing the
command:

`:pipe-to perl path/to/make_format.pl -name example -output example_log.json`

Using the `-name` or `-n` option sets the name in the format.  This is lazy,
so you'll need to edit it to suit yourself.  If this option is not specified
the format name is 'NEW' throughout.

Using the `-output` or `-o` option sets the destination for the new format.
If this is not specified the result will be written to standard output.

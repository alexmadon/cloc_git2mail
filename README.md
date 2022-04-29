# cloc_git2mail: a wrapper around cloc

This tool written in python gets some code from the Internet, count the lines of codes and mails a report;

The code only uses the python standard library and is designed to be portable across platforms (Linux, mac, Windows).

It has hover only been tested on Linux.

## Features

* a GitHub oriented handy syntax, but can also work on any archive URL
* email is sent using Gmail (so you need a Gmail account)
* configuration can be done using env variables of CLI options
* verbosity of logs can be changed (see the -d debug mode)
* unit tests can be run using the -t option
* it has a cache feature, useful if you decide you want to send the same report to some other recipient

Limitations:

* the code to analyze must be public (authentication is not supported yet)

## Installation

Just download the file `cloc_git2mail`

Or clone the repository

https://github.com/alexmadon/cloc_git2mail

You might also want to add the script location to your system PATH.

## Dependencies

The tool assumes you have python3 installed.

The tool assumes you have cloc installed.

cloc installation is detailed there:
http://cloc.sourceforge.net/
https://github.com/AlDanial/cloc



## Configuration

There are two ways to configure the analysis job:

### Using CLI arguments

The arguments are documented briefly in the CLI help:

cloc_git2mail -h

to get the help

### Using env variables

Each CLI option can also be set using env variables.

You map CLI parameter name to env variable name using the following rule:

You uppercase the parameter name, replace the dashes with underscore and prepend CLOC_

Example:

`--mailfrom-username` option is mapped to `CLOC_MAILFROM_USERNAME`

You typically want to set those variables:

```
CLOC_COMMAND=/home/madon/cloc/cloc-1.92.pl
CLOC_MAILFROM_PASSWORD=mypassword
CLOC_MAILFROM_USERNAME=mysuser@gmail.com
```

If a necessary argument is missing, then the program will ask for its value during execution.

For instance if you run:

```
cloc_git2mail AlDanial/cloc
```

and there is not variable `CLOC_MAILTO` set,
then the program will ask for the recipient email address



## Usage

Examples of usage:



```
cloc_git2mail --mailto alex.madon@gmail.com https://github.com/AlDanial/cloc
cloc_git2mail --mailto alex.madon@gmail.com github.com/AlDanial/cloc
cloc_git2mail --mailto alex.madon@gmail.com AlDanial/cloc
cloc_git2mail AlDanial/cloc
cloc_git2mail --raw https://someserver/somearchive.zip
```

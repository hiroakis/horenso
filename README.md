horenso
=======

[![Build Status](https://travis-ci.org/Songmu/horenso.png?branch=master)][travis]
[![Coverage Status](https://coveralls.io/repos/Songmu/horenso/badge.png?branch=master)][coveralls]
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)][license]

[travis]: https://travis-ci.org/Songmu/horenso
[coveralls]: https://coveralls.io/r/Songmu/horenso?branch=master
[license]: https://github.com/Songmu/horenso/blob/master/LICENSE

## Description

Command wrapper for reporting the result. It is useful cron jobs.

## Installation

    % go get github.com/Songmu/horenso/cmd/horenso

## Synopsis

    % horenso --reporter /path/to/report.pl -- /path/to/yourjob

## Options

```
Usage:
  horenso --reporter /path/to/reporter.pl -- /path/to/job [...]

Application Options:
  -r, --reporter=/path/to/reporter.pl    handler for reporting the result of the job
  -n, --noticer=/path/to/noticer.rb      handler for noticing the start of the job
  -T, --timestamp                        add timestamp to merged output
  -t, --tag=job-name                     tag of the job
```

## Execution Seqence

1. Start the command
2. [optional] Run the noticers
3. Wait to finish the command
4. Run the reporters

## JSON Argument

The reporters and noticers are accept one argument of JSON which reports command result like following.

```json
{
  "command": "perl -E 'say 1;warn \"$$\\n\";'",
  "commandArgs": [
    "perl",
    "-E",
    "say 1;warn \"$$\\n\";"
  ],
  "output": "1\n95030\n",
  "stdout": "1\n",
  "stderr": "95030\n",
  "exitCode": 0,
  "result": "command exited with code: 0",
  "pid": 95030,
  "startAt": "2015-12-28T00:37:10.494282399+09:00",
  "endAt": "2015-12-28T00:37:10.546466379+09:00"
}
```

## License

[MIT][license]

## Author

[Songmu](https://github.com/Songmu)
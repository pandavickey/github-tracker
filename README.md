# GitHub Repo Tracker

[![Build Status](https://travis-ci.org/timsneath/github-tracker.svg?branch=master)](https://travis-ci.org/timsneath/github-tracker)

Grabs useful information from GitHub. At present, this only has one command
available (but I'll probably add more over time).

| Command    | Description                                         |
|------------|-----------------------------------------------------|
| repo-stars | Provides an ordered list of the top repos on GitHub |

## Usage

Make sure you have the Dart SDK installed (<https://dartlang.org>).

The following command gives an ordered list of the top 100 repos on GitHub:

```bash
$ dart repo-stars.dart
  1  twbs/bootstrap                     125174
  2  tensorflow/tensorflow              102100
  3  facebook/react                      97742
  4  vuejs/vue                           96932
  5  d3/d3                               76338
  6  robbyrussell/oh-my-zsh              71507
  7  facebook/react-native               64757
  8  electron/electron                   61007
  9  torvalds/linux                      59445
 10  angular/angular.js                  58579
 11  FortAwesome/Font-Awesome            56580
 12  Microsoft/vscode                    52300
 ...
 90  google/protobuf                     26632
 91  gohugoio/hugo                       26193
 92  zeit/next.js                        26051
 93  flutter/flutter                     26050
 94  TryGhost/Ghost                      25882
 95  gogs/gogs                           25514
 96  spring-projects/spring-boot         25382
 97  shadowsocks/shadowsocks             25283
 98  opencv/opencv                       25260
 99  discourse/discourse                 25204
100  prettier/prettier                   25041
```

The command above also stores more detailed output from GitHub in a file
`cache.json`. Repeated invocations over the command use the cache to minimize
hitting the GitHub rate limit, although you can refresh the cache by using the
`--refresh` option, for example:

```bash
dart repo-stars.dart --refresh
```

By default, the command ignores archived and content-only repos.

You can get further usage help by running:

```bash
dart repo-stars.dart --help
```

## Known Issues

- The command uses a brute force of getting the top 300 repos with > 10,000
  stars and then filtering. We should get a count and grab the appropriate
  quantity of paginated content to fill the JSON cache as appropriate.

- More options would be nice, e.g. `--csv` to generate output suitable for
  importing into Microsoft Excel, Google Sheets etc.
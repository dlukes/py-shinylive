# Change Log for Shinylive

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).


## [0.0.8] - 2022-10-26

### New features

* Updated to Shinylive web assets 0.0.11.

### Bug fixes

* Added fix to avoid tarfile path traversal (CVE-2007-4559). (#3)


## [0.0.7] - 2022-09-26

### Library updates

* Updated to Shinylive web assets 0.0.10.


## [0.0.6] - 2022-09-21

### New features

* Updated to Shinylive web assets 0.0.9.

### Bug fixes

* Fixed bug in removal of symlinked asset directories.


## [0.0.5] - 2022-09-20

### New features

* Added `shinylive assets version` command, which prints out the version of the Shinylive web assets.

### Bug fixes

* Fixed #1: `verbose_print()` raised an error due to an extra argument.


## [0.0.4] - 2022-09-19

### New features

* Added `shinylive assets link-from-local` command.

* Print messages to stderr instead of stdout.


## [0.0.3] - 2022-09-16

### New features

* Updated command-line tool to work better with Quarto extension.


## [0.0.2] - 2022-09-02

### New features

* Changed `shinylive deploy` to `shinylive export`.

* Update to use Shinylive web assets version 0.0.7.

subcommands golang library
==========================

This package permits a Go application to implement subcommands support
similar to what is supported by the 'go' tool.

The library is designed so that the test cases can run concurrently.
Using global flags variables is discouraged to keep your program testable
conccurently.

The intended command is found via heuristic search;

  - exact match
  - unique prefix, e.g. `lo` will run `longcommand` as long as there's no
    command with the same prefix.
  - case insensitivity; for those weird enough to use Upper Cased Commands.
  - [levenshtein distance](http://en.wikipedia.org/wiki/Levenshtein_distance);
    where `longcmmand` or `longcmomand` will properly trigger `longcommand`.

[![GoDoc](https://godoc.org/github.com/maruel/subcommands?status.svg)](https://godoc.org/github.com/maruel/subcommands)
[![Build Status](https://travis-ci.org/maruel/subcommands.svg?branch=master)](https://travis-ci.org/maruel/subcommands)
[![Coverage Status](https://img.shields.io/coveralls/maruel/subcommands.svg)](https://coveralls.io/r/maruel/subcommands?branch=master)


Examples
--------

  - See `sample-simple` for a barebone sample skeleton usable as-is.
  - See `sample-complex` for a complex sample using advanced features.
  - See module `subcommands/subcommandstest` for tools to help *testing* an
    application using subcommands. One of the main benefit is t.Parallel() just
    works, because subcommands help wrapping global variables.

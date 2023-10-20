# tla-bin-macos

tla-bin is a wrapper around https://github.com/tlaplus/tlaplus that provides
command line binaries for pcal, tlc, tlatex and sany, making automation around
TLA+ easy.  Also provides a binary that starts the TLA+ REPL.

tla-bin-macos is a fork of tla-bin that assumes that the TLA+ Toolbox is already installed in /Applications.

## Installation

### Install the binaries in /opt/tla/bin

```
$ git clone https://github.com/klaeufer/tla-bin-macos.git
$ cd tla-bin-macos
$ sudo mkdir /opt/tla
$ sudo cp -a bin /opt/tla
```

### Add /opt/tla/bin to PATH

For the current shell session:

PATH=/opt/tla/bin:$PATH

To add `/opt/tla/bin` to your path permanently, use the appropriate steps for your shell.

## Usage

### `pcal`, the PlusCal → TLA+ translator

```
$ pcal Euclid.tla
pcal.trans Version 1.11 of 31 December 2020
Labels added.
Parsing completed.
Translation completed.
New file Euclid.tla written.
New file Euclid.cfg written.
```

### `tlc`, the TLA+ model checker

```
$ tlc Euclid.tla
TLC2 Version 2.16 of 31 December 2020 (rev: cdddf55)
Running breadth-first search Model-Checking with fp 70 and seed -2731419115466680819 with 1 worker on 2 cores with 444MB heap and 64MB offheap memory [pid: 1039] (Linux 4.19.0-18-amd64 amd64, Debian 11.0.12 x86_64, MSBDiskFPSet, DiskStateQueue).
Parsing file /home/pdm/tla-bin/tla/MC.tla
Parsing file /home/pdm/tla-bin/tla/Euclid.tla
Labels added.
Parsing file /tmp/TLC.tla
Parsing file /tmp/Integers.tla
Parsing file /home/pdm/tla-bin/GCD.tla
Parsing file /tmp/Naturals.tla
Parsing file /tmp/Sequences.tla
Parsing file /tmp/FiniteSets.tla
Semantic processing of module Naturals
Semantic processing of module Integers
Semantic processing of module PaulGCD
Semantic processing of module Sequences
Semantic processing of module FiniteSets
Semantic processing of module TLC
Semantic processing of module PaulEuclid
Semantic processing of module MC
Starting... (2021-11-28 16:13:57)
Computing initial states...
Finished computing initial states: 1 distinct state generated at 2021-11-28 16:13:57.
Model checking completed. No error has been found.
  Estimates of the probability that TLC did not check all reachable states
  because two distinct states had the same fingerprint:
  calculated (optimistic):  val = 2.7E-19
6 states generated, 5 distinct states found, 0 states left on queue.
The depth of the complete state graph search is 5.
The average outdegree of the complete state graph is 1 (minimum is 0, the maximum 1 and the 95th percentile is 1).
Finished in 01s at (2021-11-28 16:13:57)
```

### `sany`, the TLA+ static analyzer

```
$ sany Euclid.tla

****** SANY2 Version 2.1 created 24 February 2014

Parsing file /home/pdm/tla-bin/Euclid.tla
Labels added.
Parsing file /tmp/Integers.tla
Parsing file /home/pdm/tla-bin/GCD.tla
Parsing file /tmp/TLC.tla
Parsing file /tmp/Naturals.tla
Parsing file /tmp/Sequences.tla
Parsing file /tmp/FiniteSets.tla
Semantic processing of module Naturals
Semantic processing of module Integers
Semantic processing of module GCD
Semantic processing of module Sequences
Semantic processing of module FiniteSets
Semantic processing of module TLC
Semantic processing of module Euclid
```

### `tlatex`, the TLA+ pretty printer

```
$ tlatex Euclid.tla
tla2tex.TLA Version 1.0 created  12 Apr 2013
looking for file: Euclid
looking for file: Euclid.log
looking for file: Euclid
TLATeX dvi output written on Euclid.dvi.
Total execution time: 0.38 seconds
```

### `tlarepl`, the TLA+ REPL

(Requires TLA+ version 1.8.0 or higher, which as of November 2021 is only
found in nightly builds.)

```
$ tlarepl
Welcome to the TLA+ REPL!
TLC2 Version 2.16 of Day Month 20??
Enter a constant-level TLA+ expression.
(tla+)
```

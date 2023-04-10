# moreutils

## Description

This is a growing collection of the unix tools that nobody thought to write
thirty years ago.
So far, it includes the following utilities:
- isutf8: check if a file or standard input is utf-8
- sponge: soak up standard input and write to a file
- ts: timestamp standard input
- vidir: edit a directory in your text editor
- vipe: insert a text editor into a pipe
- combine: combine the lines in two files using boolean operations
- ifdata: get network interface info without parsing ifconfig output
- pee: tee standard input to pipes
- zrun: automatically uncompress arguments to command
- mispipe: pipe two commands, returning the exit status of the first
- lckdo: execute a program with a lock held
- ifne: run a program if the standard input is not empty
- parallel: run multiple jobs at once (contained in moreutils-parallel sub
  package)
- chronic: runs a command quietly, unless it fails

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: moreutils
  vars:
    moreutils_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: moreutils
  vars:
    moreutils_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: moreutils
  vars:
    moreutils_state: 'inactive'
```

## Parameters

### Role

`moreutils_state`

    Description: Control the state of the role.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

## Conflicts

## Dependencies

### Packages

`moreutils`

    Version: >= 0.40
    Name   :
      OpenBSD 7.2: 'moreutils'
      OpenBSD 7.3: 'moreutils'

## Parameters

## Requirements

### Control Node

`ansible`

    Version: >= 2.8.0

### Managed Node

`python`

    Version: >= 2.7.0

## Support

### Operating Systems

`openbsd`

    Version: 7.2
    Version: 7.3

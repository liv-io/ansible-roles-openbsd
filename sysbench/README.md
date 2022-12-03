# sysbench

## Description

SysBench is a modular, cross-platform and multi-threaded benchmark tool for
evaluating OS parameters that are important for a system running a database
under intensive load.
The idea of this benchmark suite is to quickly get an impression about system
performance without setting up complex database benchmarks or even without
installing a database at all. Current features allow to test the following
system parameters:
 - file I/O performance
 - scheduler performance
 - memory allocation and transfer speed
 - POSIX threads implementation performance
 - database server performance (OLTP benchmark)

Primarily written for MySQL server benchmarking, SysBench will be further
extended to support multiple database backends, distributed benchmarks and
third-party plug-in modules.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: sysbench
  vars:
    sysbench_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: sysbench
  vars:
    sysbench_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: sysbench
  vars:
    sysbench_state: 'inactive'
```

## Parameters

### Role

`sysbench_state`

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

`sysbench`

    Version: >= 0.4
    Name   :
      OpenBSD 7.1: 'sysbench--'
      OpenBSD 7.2: 'sysbench--'

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

    Version: 7.1
      Status: Stable
    Version: 7.2
      Status: Stable

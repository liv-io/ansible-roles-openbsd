# stress

## Description

stress is not a benchmark, but is rather a tool designed to put given subsytems
under a specified load. Instances in which this is useful include those in which
a system administrator wishes to perform tuning activities, a kernel or libc
programmer wishes to evaluate denial of service possibilities, etc.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: stress
  vars:
    stress_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: stress
  vars:
    stress_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: stress
  vars:
    stress_state: 'inactive'
```

## Parameters

### Role

`stress_state`

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

`stress`

    Version: >= 1.0
    Name   :
      OpenBSD 7.1: 'stress'
      OpenBSD 7.2: 'stress'

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
    Version: 7.2

# fping

## Description

fping is a ping-like program which can determine the accessibility of multiple
hosts using ICMP echo requests. fping is designed for parallelized monitoring of
large numbers of systems, and is developed with ease of use in scripting in
mind.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: fping
  vars:
    fping_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: fping
  vars:
    fping_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: fping
  vars:
    fping_state: 'inactive'
```

## Parameters

### Role

`fping_state`

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

`fping`

    Version: >= 2.4
    Name   :
      OpenBSD 7.1: 'fping'
      OpenBSD 7.2: 'fping'

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

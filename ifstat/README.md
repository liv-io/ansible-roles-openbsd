# ifstat

## Description

ifstat is a tool to report network interfaces bandwith just like vmstat/iostat
do for other system counters.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: ifstat
  vars:
    ifstat_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: ifstat
  vars:
    ifstat_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: ifstat
  vars:
    ifstat_state: 'inactive'
```

## Parameters

### Role

`ifstat_state`

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

`ifstat`

    Version: >= 1.1
    Name   :
      OpenBSD 7.1: 'ifstat--'
      OpenBSD 7.2: 'ifstat--'

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

# ncdu

## Description

ncdu (NCurses Disk Usage) is a curses-based version of the well-known 'du', and
provides a fast way to see what directories are using your disk space.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: ncdu
  vars:
    ncdu_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: ncdu
  vars:
    ncdu_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: ncdu
  vars:
    ncdu_state: 'inactive'
```

## Parameters

### Role

`ncdu_state`

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

`ncdu`

    Version: >= 1.7
    Name   :
      OpenBSD 7.2: 'ncdu'
      OpenBSD 7.3: 'ncdu'

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

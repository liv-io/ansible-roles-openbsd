# pftop

## Description

pfTop is a curses-based utility for real-time display of active states and rules
for pf. It is a cross between top and pfctl -sr and pfctl -ss.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: pftop
  vars:
    pftop_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: pftop
  vars:
    pftop_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: pftop
  vars:
    pftop_state: 'inactive'
```

## Parameters

### Role

`pftop_state`

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

`pftop`

    Version: >= 0.7
    Name   :
      OpenBSD 7.1: 'pftop'
      OpenBSD 7.2: 'pftop'

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

# arping

## Description

The arping command acts like the standard ping command except it pings a machine
by its ARP address instead of its IP address. It is typically used to locate a
machine if its hardware address is known but its IP address is unknown.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: arping
  vars:
    arping_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: arping
  vars:
    arping_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: arping
  vars:
    arping_state: 'inactive'
```

## Parameters

### Role

`arping_state`

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

`arping`

    Version: >= 2.13
    Name   :
      OpenBSD 7.1: 'arping'
      OpenBSD 7.2: 'arping'

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

# poink

## Description

Nosuid TCP/IP ping is a small, secure replacement for the original ping command.
Unlike its setuid counterpart, it won't allow flood-pings, security compromises
and other typical problems. It uses TCP syn-rst challenge/response instead of
ICMP echo and echo-reply.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: poink
  vars:
    poink_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: poink
  vars:
    poink_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: poink
  vars:
    poink_state: 'inactive'
```

## Parameters

### Role

`poink_state`

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

`poink`

    Version: >= 1.6
    Name   :
      OpenBSD 7.1: 'poink'
      OpenBSD 7.2: 'poink'

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

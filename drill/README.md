# drill

## Description

drill is a tool ala dig from BIND. It was designed with DNSSEC in mind and
should be a useful debugging/query tool for DNSSEC.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: drill
  vars:
    drill_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: drill
  vars:
    drill_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: drill
  vars:
    drill_state: 'inactive'
```

## Parameters

### Role

`drill_state`

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

`drill`

    Version: >= 1.0
    Name   :
      OpenBSD 7.1: 'drill'
      OpenBSD 7.2: 'drill'

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

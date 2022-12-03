# icmpinfo

## Description

icmpinfo is a tool for looking at the icmp messages received on the running
host.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: icmpinfo
  vars:
    icmpinfo_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: icmpinfo
  vars:
    icmpinfo_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: icmpinfo
  vars:
    icmpinfo_state: 'inactive'
```

## Parameters

### Role

`icmpinfo_state`

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

`icmpinfo`

    Version: >= 1.11
    Name   :
      OpenBSD 7.1: 'icmpinfo'
      OpenBSD 7.2: 'icmpinfo'

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

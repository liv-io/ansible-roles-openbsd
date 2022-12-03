# hping3

## Description

hping3 is a network tool able to send custom TCP/IP packets and to display
target replies like ping do with ICMP replies. hping3 can handle fragmentation,
and almost arbitrary packet size and content, using the command line interface.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: hping3
  vars:
    hping3_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: hping3
  vars:
    hping3_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: hping3
  vars:
    hping3_state: 'inactive'
```

## Parameters

### Role

`hping3_state`

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

`hping3`

    Version: >= 20051105
    Name   :
      OpenBSD 7.1: 'hping'
      OpenBSD 7.2: 'hping'

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

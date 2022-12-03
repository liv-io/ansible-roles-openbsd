# nload

## Description

nload is a console application which monitors network traffic and bandwidth
usage in real time. It visualizes the in and outgoing traffic using two graphs
and provides additional info like total amount of transfered data and min/max
network usage.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: nload
  vars:
    nload_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: nload
  vars:
    nload_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: nload
  vars:
    nload_state: 'inactive'
```

## Parameters

### Role

`nload_state`

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

`nload`

    Version: >= 0.7
    Name   :
      OpenBSD 7.1: 'nload'
      OpenBSD 7.2: 'nload'

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

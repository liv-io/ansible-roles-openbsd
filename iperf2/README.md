# iperf2

## Description

Iperf is a tool to measure maximum TCP bandwidth, allowing the tuning of various
parameters and UDP characteristics. Iperf reports bandwidth, delay jitter,
datagram loss.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: iperf2
  vars:
    iperf2_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: iperf2
  vars:
    iperf2_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: iperf2
  vars:
    iperf2_state: 'inactive'
```

## Parameters

### Role

`iperf2_state`

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

`iperf2`

    Version: >= 2.0
    Name   :
      OpenBSD 7.2: 'iperf'
      OpenBSD 7.3: 'iperf'

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

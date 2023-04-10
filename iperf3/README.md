# iperf3

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
    - role: iperf3
  vars:
    iperf3_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: iperf3
  vars:
    iperf3_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: iperf3
  vars:
    iperf3_state: 'inactive'
```

## Parameters

### Role

`iperf3_state`

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

`iperf3`

    Version: >= 3.0
    Name   :
      OpenBSD 7.2: 'iperf3'
      OpenBSD 7.3: 'iperf3'

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

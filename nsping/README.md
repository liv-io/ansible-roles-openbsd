# nsping

## Description

Nsping uses DNS queries to monitor reachability and operation of name-servers,
as well as the latency of DNS queries. It does this by sending random recursive
DNS queries to the nameserver (avoiding the effects of DNS caching) and
measuring the amount of time between the sending of the query and the receipt
of the response packet.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: nsping
  vars:
    nsping_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: nsping
  vars:
    nsping_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: nsping
  vars:
    nsping_state: 'inactive'
```

## Parameters

### Role

`nsping_state`

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

`nsping`

    Version: >= 0.8
    Name   :
      OpenBSD 7.1: 'nsping'
      OpenBSD 7.2: 'nsping'

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

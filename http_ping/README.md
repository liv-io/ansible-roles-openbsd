# http_ping

## Description

http_ping is like the regular ping command, except that it sends HTTP
requests instead of ICMP echo requests.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: http_ping
  vars:
    http_ping_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: http_ping
  vars:
    http_ping_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: http_ping
  vars:
    http_ping_state: 'inactive'
```

## Parameters

### Role

`http_ping_state`

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

`http_ping`

    Version: >= 20050629
    Name   :
      OpenBSD 7.2: 'http_ping'
      OpenBSD 7.3: 'http_ping'

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

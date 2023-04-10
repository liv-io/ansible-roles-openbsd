# http_load

## Description

http_load runs multiple HTTP fetches in parallel, to test the throughput
of a web server.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: http_load
  vars:
    http_load_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: http_load
  vars:
    http_load_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: http_load
  vars:
    http_load_state: 'inactive'
```

## Parameters

### Role

`http_load_state`

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

`http_load`

    Version: >= 20140814
    Name   :
      OpenBSD 7.2: 'http_load'
      OpenBSD 7.3: 'http_load'

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

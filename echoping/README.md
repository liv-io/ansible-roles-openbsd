# echoping

## Description

"echoping" is a small program to test (approximatively) performances of a remote
host by sending it TCP "echo" (or other protocol) packets.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: echoping
  vars:
    echoping_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: echoping
  vars:
    echoping_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: echoping
  vars:
    echoping_state: 'inactive'
```

## Parameters

### Role

`echoping_state`

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

`echoping`

    Version: >= 5.2
    Name   :
      OpenBSD 7.1: 'echoping'
      OpenBSD 7.2: 'echoping'

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

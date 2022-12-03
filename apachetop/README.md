# apachetop

## Description

ApacheTop is a curses-based top-like display for Apache information, including
requests per second, bytes per second, most popular URLs, etc.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: apachetop
  vars:
    apachetop_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: apachetop
  vars:
    apachetop_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: apachetop
  vars:
    apachetop_state: 'inactive'
```

## Parameters

### Role

`apachetop_state`

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

`apachetop`

    Version: >= 0.12
    Name   :
      OpenBSD 7.1: 'apachetop'
      OpenBSD 7.2: 'apachetop'

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

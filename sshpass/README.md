# sshpass

## Description

Tool for non-interactively performing password authentication with so called
"interactive keyboard password authentication" of SSH. Most users should use
more secure public key authentication of SSH instead.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: sshpass
  vars:
    sshpass_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: sshpass
  vars:
    sshpass_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: sshpass
  vars:
    sshpass_state: 'inactive'
```

## Parameters

### Role

`sshpass_state`

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

`sshpass`

    Version: >= 1.05
    Name   :
      OpenBSD 7.1: 'sshpass'
      OpenBSD 7.2: 'sshpass'

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

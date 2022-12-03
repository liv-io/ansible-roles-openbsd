# splint

## Description

Splint is a tool for statically checking C programs for coding errors and
security vulnerabilities. With minimal effort, Splint can be used as a better
lint. If additional effort is invested adding annotations to programs, Splint
can perform even stronger checks than can be done by any standard lint.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: splint
  vars:
    splint_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: splint
  vars:
    splint_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: splint
  vars:
    splint_state: 'inactive'
```

## Parameters

### Role

`splint_state`

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

`splint`

    Version: >= 3.1
    Name   :
      OpenBSD 7.1: 'splint'
      OpenBSD 7.2: 'splint'

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

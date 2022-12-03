# colorls

## Description

ls that can use color to display file attributes.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: colorls
  vars:
    colorls_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: colorls
  vars:
    colorls_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: colorls
  vars:
    colorls_state: 'inactive'
```

## Parameters

### Role

`colorls_state`

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

`colorls`

    Version: >= 5.7
    Name   :
      OpenBSD 7.1: 'colorls'
      OpenBSD 7.2: 'colorls'

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

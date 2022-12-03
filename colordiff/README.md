# colordiff

## Description

Colordiff is a wrapper for diff and produces the same output but with pretty
syntax highlighting. Color schemes can be customized.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: colordiff
  vars:
    colordiff_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: colordiff
  vars:
    colordiff_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: colordiff
  vars:
    colordiff_state: 'inactive'
```

## Parameters

### Role

`colordiff_state`

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

`colordiff`

    Version: >= 1.0
    Name   :
      OpenBSD 7.1: 'colordiff'
      OpenBSD 7.2: 'colordiff'

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

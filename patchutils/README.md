# patchutils

## Description

This is a collection of programs that can manipulate patch files in a variety of
ways, such as interpolating between two pre-patches, combining two incremental
patches, fixing line numbers in hand-edited patches, and simply listing the
files modified by a patch.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: patchutils
  vars:
    patchutils_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: patchutils
  vars:
    patchutils_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: patchutils
  vars:
    patchutils_state: 'inactive'
```

## Parameters

### Role

`patchutils_state`

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

`patchutils`

    Version: >= 0.3
    Name   :
      OpenBSD 7.2: 'patchutils'
      OpenBSD 7.3: 'patchutils'

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

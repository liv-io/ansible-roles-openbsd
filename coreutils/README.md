# coreutils

## Description

These are the GNU core utilities. This package is the combination of the old GNU
fileutils, sh-utils, and textutils packages.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: coreutils
  vars:
    coreutils_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: coreutils
  vars:
    coreutils_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: coreutils
  vars:
    coreutils_state: 'inactive'
```

## Parameters

### Role

`coreutils_state`

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

`coreutils`

    Version: >= 8.2
    Name   :
      OpenBSD 7.1: 'coreutils'
      OpenBSD 7.2: 'coreutils'

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

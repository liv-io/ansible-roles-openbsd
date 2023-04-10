# git

## Description

Git is a fast, scalable, distributed revision control system with an unusually
rich command set that provides both high-level operations and full access to
internals.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: git
  vars:
    git_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: git
  vars:
    git_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: git
  vars:
    git_state: 'inactive'
```

## Parameters

### Role

`git_state`

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

`git`

    Version: >= 1.7
    Name   :
      OpenBSD 7.2: 'git'
      OpenBSD 7.3: 'git'

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

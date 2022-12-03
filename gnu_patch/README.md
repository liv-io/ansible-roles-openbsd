# gnu_patch

## Description

GNU patch is the Free Software Foundation's version of the patch command. Patch
takes a patch file containing a difference listing produced by the diff program
and applies those differences to one or more original files, producing patched
versions.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: gnu_patch
  vars:
    gnu_patch_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: gnu_patch
  vars:
    gnu_patch_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: gnu_patch
  vars:
    gnu_patch_state: 'inactive'
```

## Parameters

### Role

`gnu_patch_state`

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

`gnu-patch`

    Version: >= 2.7
    Name   :
      OpenBSD 7.1: 'gpatch'
      OpenBSD 7.2: 'gpatch'

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

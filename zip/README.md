# zip

## Description

The zip program is a compression and file packaging utility. Zip is analogous to
a combination of the UNIX tar and compress commands and is compatible with PKZIP
(a compression and file packaging utility for MS-DOS systems).

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: zip
  vars:
    zip_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: zip
  vars:
    zip_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: zip
  vars:
    zip_state: 'inactive'
```

## Parameters

### Role

`zip_state`

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

`zip`

    Version: >= 3.0
    Name   :
      OpenBSD 7.1: 'zip'
      OpenBSD 7.2: 'zip'

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

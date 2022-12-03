# unzip

## Description

The unzip utility is used to list, test, or extract files from a zip archive.
Zip archives are commonly found on MS-DOS systems. The zip utility, included in
the zip package, creates zip archives. Zip and unzip are both compatible with
archives created by PKWARE(R)'s PKZIP for MS-DOS, but the programs' options and
default behaviors do differ in some respects.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: unzip
  vars:
    unzip_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: unzip
  vars:
    unzip_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: unzip
  vars:
    unzip_state: 'inactive'
```

## Parameters

### Role

`unzip_state`

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

`unzip`

    Version: >= 6.0
    Name   :
      OpenBSD 7.1: 'unzip--'
      OpenBSD 7.2: 'unzip--'

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

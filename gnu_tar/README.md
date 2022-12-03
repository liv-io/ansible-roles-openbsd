# gnu_tar

## Description

The Free Software Foundation's tape archiver. GNU tar saves many files together
into a single tape or disk archive, and can restore individual files from the
archive. It includes multivolume support, the ability to archive sparse files,
automatic archive compression/decompression, remote archives and special
features that allow tar to be used for incremental and full backups. This
distribution also includes rmt, the remote tape server.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: gnu_tar
  vars:
    gnu_tar_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: gnu_tar
  vars:
    gnu_tar_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: gnu_tar
  vars:
    gnu_tar_state: 'inactive'
```

## Parameters

### Role

`gnu_tar_state`

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

`gnu-tar`

    Version: >= 1.28
    Name   :
      OpenBSD 7.1: 'gtar--'
      OpenBSD 7.2: 'gtar--'

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

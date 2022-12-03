# rsync

## Description

Rsync uses a reliable algorithm to bring remote and host files into sync very
quickly. Rsync is fast because it just sends the differences in the files over
the network instead of sending the complete files. Rsync is often used as a very
powerful mirroring process or just as a more capable replacement for the rcp
command. A technical report which describes the rsync algorithm is included in
this package.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: rsync
  vars:
    rsync_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: rsync
  vars:
    rsync_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: rsync
  vars:
    rsync_state: 'inactive'
```

## Parameters

### Role

`rsync_state`

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

`rsync`

    Version: >= 3.0
    Name   :
      OpenBSD 7.1: 'rsync--'
      OpenBSD 7.2: 'rsync--'

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

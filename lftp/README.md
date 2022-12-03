# lftp

## Description

LFTP is a sophisticated ftp/http file transfer program. Like bash, it has job
control and uses the readline library for input. It has bookmarks, built-in
mirroring, and can transfer several files in parallel. It is designed with
reliability in mind.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: lftp
  vars:
    lftp_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: lftp
  vars:
    lftp_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: lftp
  vars:
    lftp_state: 'inactive'
```

## Parameters

### Role

`lftp_state`

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

`lftp`

    Version: >= 4.0
    Name   :
      OpenBSD 7.1: 'lftp'
      OpenBSD 7.2: 'lftp'

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

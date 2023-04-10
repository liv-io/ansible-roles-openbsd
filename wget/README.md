# wget

## Description

GNU Wget is a file retrieval utility which can use either the HTTP or FTP
protocols. Wget features include the ability to work in the background while you
are logged out, recursive retrieval of directories, file name wildcard matching,
remote file timestamp storage and comparison, use of Rest with FTP servers and
Range with HTTP servers to retrieve files over slow or unstable connections,
support for Proxy servers, and configurability.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: wget
  vars:
    wget_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: wget
  vars:
    wget_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: wget
  vars:
    wget_state: 'inactive'
```

## Parameters

### Role

`wget_state`

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

`wget`

    Version: >= 1.12
    Name   :
      OpenBSD 7.2: 'wget'
      OpenBSD 7.3: 'wget'

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

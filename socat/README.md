# socat

## Description

Socat is a relay for bidirectional data transfer between two independent data
channels. Each of these data channels may be a file, pipe, device (serial line
etc. or a pseudo terminal), a socket (UNIX, IP4, IP6 - raw, UDP, TCP), an SSL
socket, proxy CONNECT connection, a file descriptor (stdin etc.), the GNU line
editor (readline), a program, or a combination of two of these.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: socat
  vars:
    socat_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: socat
  vars:
    socat_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: socat
  vars:
    socat_state: 'inactive'
```

## Parameters

### Role

`socat_state`

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

`socat`

    Version: >= 1.7.2.3
    Name   :
      OpenBSD 7.1: 'socat'
      OpenBSD 7.2: 'socat'

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

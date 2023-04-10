# dsniff

## Description

A collection of tools for network auditing and penetration testing. Dsniff,
filesnarf, mailsnarf, msgsnarf, urlsnarf and webspy allow to passively monitor
a network for interesting data (passwords, e-mail, files). Arpspoof, dnsspoof
and macof facilitate the interception of network traffic normally unavailable
to an attacker (e.g, due to layer-2 switching). Sshmitm and webmitm implement
active monkey-in-the-middle attacks against redirected SSH and HTTPS sessions
by exploiting weak bindings in ad-hoc PKI.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: dsniff
  vars:
    dsniff_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: dsniff
  vars:
    dsniff_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: dsniff
  vars:
    dsniff_state: 'inactive'
```

## Parameters

### Role

`dsniff_state`

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

`dsniff`

    Version: >= 2.4
    Name   :
      OpenBSD 7.2: 'dsniff--no_x11'
      OpenBSD 7.3: 'dsniff--no_x11'

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

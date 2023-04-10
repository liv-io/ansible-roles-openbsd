# python_paramiko

## Description

Paramiko (a combination of the esperanto words for "paranoid" and "friend") is
a module for python 2.3 or greater that implements the SSH2 protocol for secure
(encrypted and authenticated) connections to remote machines. Unlike SSL (aka
TLS), the SSH2 protocol does not require heirarchical certificates signed by a
powerful central authority. You may know SSH2 as the protocol that replaced
telnet and rsh for secure access to remote shells, but the protocol also
includes the ability to open arbitrary channels to remote services across an
encrypted tunnel. (This is how sftp works, for example.)

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: python_paramiko
  vars:
    python_paramiko_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: python_paramiko
  vars:
    python_paramiko_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: python_paramiko
  vars:
    python_paramiko_state: 'inactive'
```

## Parameters

### Role

`python_paramiko_state`

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

`python-paramiko`

    Version: >= 2.11
    Name   :
      OpenBSD 7.2: 'py3-paramiko'
      OpenBSD 7.3: 'py3-paramiko'

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

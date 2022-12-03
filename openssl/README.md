# openssl

## Description

The OpenSSL toolkit provides support for secure communications between machines.
OpenSSL includes a certificate management tool and shared libraries which
provide various cryptographic algorithms and protocols.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: openssl
  vars:
    openssl_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: openssl
  vars:
    openssl_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: openssl
  vars:
    openssl_state: 'inactive'
```

## Parameters

### Role

`openssl_state`

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

`openssl`

    Version: >= 1.0
    Name   :
      OpenBSD 7.1: 'openssl'
      OpenBSD 7.2: 'openssl'

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

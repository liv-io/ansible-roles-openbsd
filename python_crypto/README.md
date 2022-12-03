# python_crypto

## Description

PyCrypto is a collection of both secure hash functions (such as MD5 and SHA),
and various encryption algorithms (AES, DES, RSA, ElGamal, etc.).

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: python_crypto
  vars:
    python_crypto_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: python_crypto
  vars:
    python_crypto_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: python_crypto
  vars:
    python_crypto_state: 'inactive'
```

## Parameters

### Role

`python_crypto_state`

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

`python-crypto`

    Version: >= 2.0
    Name   :
      OpenBSD 7.1: 'py-crypto'
      OpenBSD 7.2: 'py-crypto'

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

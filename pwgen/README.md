# pwgen

## Description

pwgen generates random, meaningless but pronounceable passwords. These passwords
contain either only lowercase letters, or upper and lower case, or upper case,
lower case and numeric digits. Upper case letters and numeric digits are placed
in a way that eases memorizing the password.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: pwgen
  vars:
    pwgen_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: pwgen
  vars:
    pwgen_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: pwgen
  vars:
    pwgen_state: 'inactive'
```

## Parameters

### Role

`pwgen_state`

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

`pwgen`

    Version: >= 2.06
    Name   :
      OpenBSD 7.1: 'pwgen'
      OpenBSD 7.2: 'pwgen'

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

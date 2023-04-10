# pciutils

## Description

The pciutils package contains various utilities for inspecting and setting
devices connected to the PCI bus. The utilities provided require kernel version
2.1.82 or newer (which support the /proc/bus/pci interface).

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: pciutils
  vars:
    pciutils_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: pciutils
  vars:
    pciutils_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: pciutils
  vars:
    pciutils_state: 'inactive'
```

## Parameters

### Role

`pciutils_state`

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

`pciutils`

    Version: >= 3.1
    Name   :
      OpenBSD 7.2: 'pciutils'
      OpenBSD 7.3: 'pciutils'

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

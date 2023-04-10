# usbutils

## Description

This package contains utilities for inspecting devices connected to a USB bus.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: usbutils
  vars:
    usbutils_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: usbutils
  vars:
    usbutils_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: usbutils
  vars:
    usbutils_state: 'inactive'
```

## Parameters

### Role

`usbutils_state`

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

`usbutils`

    Version: >= 007p0
    Name   :
      OpenBSD 7.2: 'usbutils'
      OpenBSD 7.3: 'usbutils'

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

# picocom

## Description

Picocom is a minimal dumb-terminal emulation program. It was designed to serve
as a simple, manual, modem configuration, testing, and debugging tool. Picocom
is ideal for embedded systems since its memory footprint is minimal (less than
20K, when stripped).

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: picocom
  vars:
    picocom_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: picocom
  vars:
    picocom_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: picocom
  vars:
    picocom_state: 'inactive'
```

## Parameters

### Role

`picocom_state`

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

`picocom`

    Version: >= 1.7
    Name   :
      OpenBSD 7.1: 'picocom'
      OpenBSD 7.2: 'picocom'

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

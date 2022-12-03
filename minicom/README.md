# minicom

## Description

Minicom is a simple text-based modem control and terminal emulation program
somewhat similar to MSDOS Telix. Minicom includes a dialing directory, full ANSI
and VT100 emulation, an (external) scripting language, and other features.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: minicom
  vars:
    minicom_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: minicom
  vars:
    minicom_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: minicom
  vars:
    minicom_state: 'inactive'
```

## Parameters

### Role

`minicom_state`

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

`minicom`

    Version: >= 2.3
    Name   :
      OpenBSD 7.1: 'minicom'
      OpenBSD 7.2: 'minicom'

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

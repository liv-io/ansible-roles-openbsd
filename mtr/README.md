# mtr

## Description

Mtr is a network diagnostic tool that combines ping and traceroute into one
program. Mtr provides two interfaces: an ncurses interface, useful for using Mtr
from a telnet session; and a GTK+ interface for X (provided in the mtr-gtk
package).

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: mtr
  vars:
    mtr_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: mtr
  vars:
    mtr_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: mtr
  vars:
    mtr_state: 'inactive'
```

## Parameters

### Role

`mtr_state`

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

`mtr`

    Version: >= 0.75
    Name   :
      OpenBSD 7.1: 'mtr--'
      OpenBSD 7.2: 'mtr--'

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

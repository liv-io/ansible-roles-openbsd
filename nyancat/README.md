# nyancat

## Description

This is an animated, color, ANSI-text telnet server that renders a loop of the
classic nyan cat animation.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: nyancat
  vars:
    nyancat_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: nyancat
  vars:
    nyancat_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: nyancat
  vars:
    nyancat_state: 'inactive'
```

## Parameters

### Role

`nyancat_state`

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

`nyancat`

    Version: >= 1.2
    Name   :
      OpenBSD 7.1: 'nyancat'
      OpenBSD 7.2: 'nyancat'

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

# gnu_watch

## Description

GNU watch runs a command repeatedly, displaying its output (the first
screenfull). This allows you to watch the program output change over time.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: gnu_watch
  vars:
    gnu_watch_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: gnu_watch
  vars:
    gnu_watch_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: gnu_watch
  vars:
    gnu_watch_state: 'inactive'
```

## Parameters

### Role

`gnu_watch_state`

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

`gnu-watch`

    Version: >= 3.2
    Name   :
      OpenBSD 7.1: 'gnuwatch'
      OpenBSD 7.2: 'gnuwatch'

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

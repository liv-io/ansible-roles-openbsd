# tmux

## Description

tmux is a "terminal multiplexer." It enables a number of terminals (or windows)
to be accessed and controlled from a single terminal. tmux is intended to be a
simple, modern, BSD-licensed alternative to programs such as GNU Screen.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: tmux
  vars:
    tmux_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: tmux
  vars:
    tmux_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: tmux
  vars:
    tmux_state: 'inactive'
```

## Parameters

### Role

`tmux_state`

    Description: Control the state of the role.
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

## Requirements

### Control Node

`ansible`

    Version: >= 2.15.0

### Managed Node

`python`

    Version: >= 3.10.0

## Support

### Operating Systems

`openbsd`

    Version: 7.6
    Version: 7.7

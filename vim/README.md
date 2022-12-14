# vim

## Description

VIM (VIsual editor iMproved) is an updated and improved version of the vi
editor. Vi was the first real screen-based editor for UNIX, and is still very
popular. VIM improves on vi by adding new features: multiple windows,
multi-level undo, block highlighting and more. The vim-enhanced package contains
a version of VIM with extra, recently introduced features like Python and Perl
interpreters.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: vim
  vars:
    vim_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: vim
  vars:
    vim_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: vim
  vars:
    vim_state: 'inactive'
```

## Parameters

### Role

`vim_state`

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

`vim`

    Version: >= 7.2
    Name   :
      OpenBSD 7.1: 'vim--no_x11'
      OpenBSD 7.2: 'vim--no_x11'

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

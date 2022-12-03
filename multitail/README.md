# multitail

## Description

MultiTail lets you view one or multiple files like the original tail program.
The difference is that it creates multiple windows on your console
(with ncurses). It can also monitor wildcards: if another file matching the
wildcard has a more recent modification date, it will automatically switch to
that file. That way you can, for example, monitor a complete directory of files.
Merging of 2 or even more logfiles is possible. It can also use colors while
displaying the logfiles (through regular expressions), for faster recognition of
what is important and what not. Multitail can also filter lines
(again with regular expressions) and has interactive menus for editing given
regular expressions and deleting and adding windows. One can also have windows
with the output of shell scripts and other software. When viewing the output of
external software, MultiTail can mimic the functionality of tools like 'watch'
and such.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: multitail
  vars:
    multitail_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: multitail
  vars:
    multitail_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: multitail
  vars:
    multitail_state: 'inactive'
```

## Parameters

### Role

`multitail_state`

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

`multitail`

    Version: >= 5.2
    Name   :
      OpenBSD 7.1: 'multitail'
      OpenBSD 7.2: 'multitail'

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

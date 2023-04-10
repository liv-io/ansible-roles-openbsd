# nano

## Description

GNU nano is a small and friendly text editor.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: nano
  vars:
    nano_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: nano
  vars:
    nano_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: nano
  vars:
    nano_state: 'inactive'
```

## Parameters

### Role

`nano_state`

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

`nano`

    Version: >= 2.0
    Name   :
      OpenBSD 7.2: 'nano'
      OpenBSD 7.3: 'nano'

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

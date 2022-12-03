# signify

## Description

The signify utility creates and verifies cryptographic signatures. A signature
verifies the integrity of a message.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: signify
  vars:
    signify_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: signify
  vars:
    signify_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: signify
  vars:
    signify_state: 'inactive'
```

## Parameters

### Role

`signify_state`

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

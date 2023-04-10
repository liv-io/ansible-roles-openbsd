# ldns

## Description

Ldns is a library to simplify implementation of recent DNS RFCs. The goal is to
allow depelopers to easily create software conforming to current RFCs and
experimental software for current Internet drafts. Because ldns is written in C
it should be a lot faster than Perl or other scripting languages.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: ldns
  vars:
    ldns_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: ldns
  vars:
    ldns_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: ldns
  vars:
    ldns_state: 'inactive'
```

## Parameters

### Role

`ldns_state`

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

`ldns`

    Version: >= 1.0
    Name   :
      OpenBSD 7.2: 'ldns-utils'
      OpenBSD 7.3: 'ldns-utils'

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

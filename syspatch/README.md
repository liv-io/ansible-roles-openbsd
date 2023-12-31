# syspatch

## Description

installurl - OpenBSD mirror server location

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: syspatch
  vars:
    syspatch_state: 'install'
    syspatch_installurl:
      - {url: 'https://ftp.eu.openbsd.org/pub/OpenBSD', comment: 'OpenBSD Packages'}
```

### Remove

```
- hosts: all
  roles:
    - role: syspatch
  vars:
    syspatch_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: syspatch
  vars:
    syspatch_state: 'inactive'
```

## Parameters

### Role

`syspatch_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

`syspatch_installurl`

    Description: Define the 'syspatch_installurl' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{url: 'https://ftp.OpenBSD.org/pub/OpenBSD', comment: 'OpenBSD Packages'}]
    Options    :
      Examples: [{url: 'https://ftp.eu.openbsd.org/pub/OpenBSD', comment 'OpenBSD Packages - EU1'},
                       'https://ftp2.eu.openbsd.org/pub/OpenBSD', comment: 'OpenBSD Packages - EU2'}]
      None    : []

## Conflicts

## Dependencies

### Roles

`signify`

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

    Version: 7.3
    Version: 7.4

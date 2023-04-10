# openbsd_syspatch

## Description

installurl - OpenBSD mirror server location

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: openbsd_syspatch
  vars:
    openbsd_syspatch_state: 'install'
    openbsd_syspatch_installurl:
      - {url: 'https://ftp.eu.openbsd.org/pub/OpenBSD', comment: 'OpenBSD Packages'}
```

### Remove

```
- hosts: all
  roles:
    - role: openbsd_syspatch
  vars:
    openbsd_syspatch_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: openbsd_syspatch
  vars:
    openbsd_syspatch_state: 'inactive'
```

## Parameters

### Role

`openbsd_syspatch_state`

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

`openbsd_syspatch_installurl`

    Description: Define the 'openbsd_syspatch_installurl' option.
    Implemented: 3.0.0
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

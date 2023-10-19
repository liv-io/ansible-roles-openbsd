# openbsd_periodic

## Description

daily, weekly, monthly - periodic system maintenance

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: openbsd_periodic
  vars:
    openbsd_periodic_state: 'install'
    openbsd_periodic_daily_state: True
    openbsd_periodic_monthly_state: True
    openbsd_periodic_weekly_state: True
```

### Remove

```
- hosts: all
  roles:
    - role: openbsd_periodic
  vars:
    openbsd_periodic_state: 'remove'
    openbsd_periodic_daily_state: True
    openbsd_periodic_monthly_state: True
    openbsd_periodic_weekly_state: True
```

### Inactive

```
- hosts: all
  roles:
    - role: openbsd_periodic
  vars:
    openbsd_periodic_state: 'inactive'
```

## Parameters

### Role

`openbsd_periodic_state`

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

`openbsd_periodic_daily_state`

    Description: Control the 'openbsd_periodic_daily_state' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openbsd_periodic_monthly_state`

    Description: Control the 'openbsd_periodic_monthly_state' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openbsd_periodic_weekly_state`

    Description: Control the 'openbsd_periodic_weekly_state' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Boolean
    Default    : False
    Options    : True | False

## Conflicts

## Dependencies

## Parameters

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

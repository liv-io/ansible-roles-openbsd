# periodic

## Description

daily, weekly, monthly - periodic system maintenance

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: periodic
  vars:
    periodic_state: 'install'
    periodic_daily_state: True
    periodic_monthly_state: True
    periodic_weekly_state: True
```

### Remove

```
- hosts: all
  roles:
    - role: periodic
  vars:
    periodic_state: 'remove'
    periodic_daily_state: True
    periodic_monthly_state: True
    periodic_weekly_state: True
```

### Inactive

```
- hosts: all
  roles:
    - role: periodic
  vars:
    periodic_state: 'inactive'
```

## Parameters

### Role

`periodic_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

`periodic_daily_state`

    Description: Control the 'periodic_daily_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`periodic_monthly_state`

    Description: Control the 'periodic_monthly_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`periodic_weekly_state`

    Description: Control the 'periodic_weekly_state' option.
    Required   : False
    Value      : Arbitrary
    Type       : Boolean
    Default    : False
    Options    : True | False

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

    Version: 7.3
    Version: 7.4

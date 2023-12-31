# hostname

## Description

The hostname utility is used to set or print the name of the current host.
If no argument is given, the name of the current host is printed.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: hostname
  vars:
    host_state: 'install'
    hostname_hostname: 'nameserver01'
```

### Inactive

```
- hosts: all
  roles:
    - role: hostname
  vars:
    host_state: 'inactive'
```

## Parameters

### Role

`hostname_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Inactive: 'quiesce' | 'inactive'

`hostname_hostname`

    Description: Define the hostname of the system.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "{{inventory_hostname}}"
    Options    :
      Examples: 'proxy' | 'nameserver' | 'webserver'

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

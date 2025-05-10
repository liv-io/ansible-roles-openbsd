# sysctl

## Description

The sysctl utility retrieves kernel state and allows processes with appropriate
privilege to set kernel state. The state to be retrieved or set is described
using a "Management Information Base" (MIB) style name, described as a dotted
set of components.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: sysctl
  vars:
    sysctl_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: sysctl
  vars:
    sysctl_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: sysctl
  vars:
    sysctl_state: 'inactive'
```

### Config

```
vars:
  sysctl_config_all:
    - key: 'net.inet.carp.preempt'
      state: True
      value: '1'

    - key: 'net.inet.carp.allow'
      state: True
      value: '1'

  sysctl_config_group:
    - key: 'net.inet.ip.ttl'
      state: False
      value: '64'

  sysctl_config_host:
    - key: 'kern.hostname'
      state: True
      value: 'host.domain.tld'
```

## Parameters

### Role

`sysctl_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

`sysctl_config_all`

    Description: Define the 'sysctl_config_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{key: 'net.inet.carp.preempt', value: '1'},
                 {key: 'net.inet.carp.allow', value: '1'}]
      None    : []

`sysctl_config_dependencies`

    Description: Define the 'sysctl_config_dependencies' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{key: 'net.inet.carp.preempt', value: '1'},
                 {key: 'net.inet.carp.allow', value: '1'}]
      None    : []

`sysctl_config_group`

    Description: Define the 'sysctl_config_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{key: 'net.inet.carp.preempt', value: '1'},
                 {key: 'net.inet.carp.allow', value: '1'}]
      None    : []

`sysctl_config_host`

    Description: Define the 'sysctl_config_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{key: 'net.inet.carp.preempt', value: '1'},
                 {key: 'net.inet.carp.allow', value: '1'}]
      None    : []

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

    Version: 7.6
    Version: 7.7

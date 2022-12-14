# openbsd_rc

## Description

The rc utility is the command script which controls the automatic boot process
after being called by init.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: openbsd_rc
  vars:
    openbsd_rc_state: 'install'
```

### Inactive

```
- hosts: all
  roles:
    - role: openbsd_rc
  vars:
    openbsd_rc_state: 'inactive'
```

### Config

```
vars:
  openbsd_rc_config_all:
    - name: 'dhcpd_flags'
      value: 'NO'
      state: 'true'
      comment: "Disable service 'dhcpd'"

  openbsd_rc_config_group:
    - name: 'nfs_server'
      value: 'YES'
      state: 'true'
      comment: 'Enable the NFS server'

  openbsd_rc_config_host:
    - name: 'nfsd_flags'
      value: '-tun 8'
      state: 'true'
      comment: 'Start 4 copies of the NFS server'
```

## Parameters

### Config

`state`

    Description: Control the state of the 'rc' entry.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'true'
    Options    :
      Install: 'true' | 'yes' | 'install'
      Remove : 'false' | 'no' | 'remove'

`comment`

    Description: Define a comment for the 'rc' entry.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'Configure service' | 'Enable service' | 'Disable service'
      None    : ''

`name`

    Description: Define the name of the 'rc' entry.
    Implemented: 0.1.0
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'sshd_class' | 'sshd_flags' | 'nfs_server' | 'nfsd_flags'

`path`

    Description: Define the path of the 'rc' file.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '/etc/rc.conf.local'
    Options    :
      Examples: '/etc/rc.conf.local'

`value`

    Description: Define the value of the 'rc' entry.
    Implemented: 0.1.0
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'YES' | 'NO' | 'root' | '30'

### Role

`openbsd_rc_state`

    Description: Control the state of the role.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Inactive: 'quiesce' | 'inactive'

`openbsd_rc_config_all`

    Description: Define the 'openbsd_rc_config_all' option.
    Implemented: 3.0.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'nfs_server', value: 'YES', state: 'true', comment: 'Enable the NFS server'},
                 {name: 'nfsd_flags', value: '-tun 8', state: 'true', comment: 'Start 4 copies of the NFS server'}]
      None    : []

`openbsd_rc_config_group`

    Description: Define the 'openbsd_rc_config_group' option.
    Implemented: 3.0.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'nfs_server', value: 'YES', state: 'true', comment: 'Enable the NFS server'},
                 {name: 'nfsd_flags', value: '-tun 8', state: 'true', comment: 'Start 4 copies of the NFS server'}]
      None    : []

`openbsd_rc_config_host`

    Description: Define the 'openbsd_rc_config_host' option.
    Implemented: 3.0.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'nfs_server', value: 'YES', state: 'true', comment: 'Enable the NFS server'},
                 {name: 'nfsd_flags', value: '-tun 8', state: 'true', comment: 'Start 4 copies of the NFS server'}]
      None    : []

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

# hosts

## Description

'/etc/hosts' is a simple text file that associates IP addresses with hostnames,
one line per IP address.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: hosts
  vars:
    hosts_state: 'install'
```

### Inactive

```
- hosts: all
  roles:
    - role: hosts
  vars:
    hosts_state: 'inactive'
```

### Config

```
vars:
  hosts_config_all:
    - name: 'host01.domain.tld'
      state: True
      ip: '192.168.1.1'
      aliases: ['host01', 'hostname01.domain.tld', 'hostname01']
      comment: 'host01'

    - name: 'host02.domain.tld'
      state: True
      ip: '192.168.1.2'
      aliases: ['host02', 'hostname02.domain.tld', 'hostname02']
      comment: 'host02'

  hosts_config_group:
    - name: 'host03.domain.tld'
      state: True
      ip: '192.168.1.3'
      aliases: ['host03', 'hostname03.domain.tld', 'hostname03']
      comment: 'host03'

  hosts_config_host:
    - name: 'host04.domain.tld'
      state: False
      ip: '192.168.1.4'
      aliases: ['host04', 'hostname04.domain.tld', 'hostname04']
      comment: 'host04'
```

## Parameters

### Config

`state`

    Description: Control the state of the hosts entry.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`name`

    Description: Define the hostname of the hosts entry.
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'host01' | 'host02' | 'host03' | 'host04'

`aliases`

    Description: Define the aliases for the hosts entry.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: ['alias01'] |
                ['alias01', 'alias02'] |
                ['alias01', 'alias02', 'alias03'] |
                ['alias01', 'alias02', 'alias03', 'alias04']
      None    : []

`comment`

    Description: Define a comment for the hosts entry.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "{{host.name}}"
    Options    :
      Examples: 'Example Host' | 'Test Host' | 'Service Host'
      None    : ''

`ip`

    Description: Define the ip of the hosts entry.
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: '192.168.1.1' | '192.168.1.2' | '192.168.1.3' | '192.168.1.4'

`path`

    Description: Define the path of the hosts file.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '/etc/hosts'
    Options    :
      Examples: '/etc/hosts'

### Role

`hosts_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Inactive: 'quiesce' | 'inactive'

`hosts_config_all`

    Description: Define the 'hosts_config_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'host01.domain.tld', state: True, ip: '192.168.1.1',
                  aliases: {'host01', 'hostname01.domain.tld', 'hostname01'}, comment: 'host01'},
                 {name: 'host02.domain.tld', state: True, ip: '192.168.1.2',
                  aliases: ['host02', 'hostname02.domain.tld', 'hostname02'], comment: 'host02'}]
      None    : []

`hosts_config_group`

    Description: Define the 'hosts_config_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'host01.domain.tld', state: True, ip: '192.168.1.1',
                  aliases: {'host01', 'hostname01.domain.tld', 'hostname01'}, comment: 'host01'},
                 {name: 'host02.domain.tld', state: True, ip: '192.168.1.2',
                  aliases: ['host02', 'hostname02.domain.tld', 'hostname02'], comment: 'host02'}]
      None    : []

`hosts_config_host`

    Description: Define the 'hosts_config_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'host01.domain.tld', state: True, ip: '192.168.1.1',
                  aliases: {'host01', 'hostname01.domain.tld', 'hostname01'}, comment: 'host01'},
                 {name: 'host02.domain.tld', state: True, ip: '192.168.1.2',
                  aliases: ['host02', 'hostname02.domain.tld', 'hostname02'], comment: 'host02'}]
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

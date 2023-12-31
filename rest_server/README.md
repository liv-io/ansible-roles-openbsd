# rest_server

## Description

Rest Server is a high performance HTTP server that implements restic's REST
backend API.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: rest_server
  vars:
    rest_server_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: rest_server
  vars:
    rest_server_state: 'enable'
```

### Disable

```
- hosts: all
  roles:
    - role: rest_server
  vars:
    rest_server_state: 'disable'
```

### Remove

```
- hosts: all
  roles:
    - role: rest_server
  vars:
    rest_server_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: rest_server
  vars:
    rest_server_state: 'inactive'
```

## Parameters

### Role

`rest_server_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'enable'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Enable  : 'start' | 'on' | 'enable'
      Disable : 'stop' | 'off' | 'disable'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

`rest_server_monitor_monit_state`

    Description: Control the 'rest_server_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`rest_server_options`

    Description: Define the 'rest_server_options' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['--path /data/rest-server', '--prometheus', '--no-auth']
    Options    :
      Examples: ['--prometheus'] | ['--path /data/restic', '--prometheus']
      None    : []

`rest_server_version`

    Description: Define the 'rest_server_version' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '0.12.0'
    Options    :
      Examples: '0.9.5' | '0.9.6'

## Conflicts

## Dependencies

### Archives

`rest-server`

### Packages

`gnu-tar`

    Version: >= 1.28
    Name   :
      OpenBSD 7.3: 'gtar--'
      OpenBSD 7.4: 'gtar--'

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

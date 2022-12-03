# openbsd_syslogd

## Description

syslogd writes system messages to log files or a user's terminal. Output can be
sent to other programs for further processing. It can also securely send and
receive log messages to and from remote hosts.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: openbsd_syslogd
  vars:
    openbsd_syslogd_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: openbsd_syslogd
  vars:
    openbsd_syslogd_state: 'enable'
    openbsd_syslogd_server: 'tcp4://log.example.com:514'
```

### Disable

```
- hosts: all
  roles:
    - role: openbsd_syslogd
  vars:
    openbsd_syslogd_state: 'disable'
    openbsd_syslogd_server: 'tcp4://log.example.com:514'
```

### Remove

```
- hosts: all
  roles:
    - role: openbsd_syslogd
  vars:
    openbsd_syslogd_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: openbsd_syslogd
  vars:
    openbsd_syslogd_state: 'inactive'
```

## Parameters

### Role

`openbsd_syslogd_state`

    Description: Control the state of the role.
    Implemented: 0.1.0
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

`openbsd_syslogd_monitor_monit_state`

    Description: Control the 'openbsd_syslogd_monitor_monit_state' option.
    Implemented: 0.2.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'false'
    Options    :
      Enable : 'true' | 'yes' | 'enable'
      Disable: 'false' | 'no' | 'disable'

`openbsd_syslogd_role`

    Description: Set the 'openbsd_syslogd_role' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'client'
    Options    :
      Client: 'client'

`openbsd_syslogd_server`

    Description: Define the 'openbsd_syslogd_server' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "tcp4://log.{{ansible_domain}}:514"
    Options    :
      Examples: 'tcp4://log.example.com:514' | 'tcp6://logs.example.com:514'
      None    : ''

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

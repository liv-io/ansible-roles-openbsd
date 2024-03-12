# syslogd

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
    - role: syslogd
  vars:
    syslogd_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: syslogd
  vars:
    syslogd_state: 'enable'
    syslogd_server: 'tcp4://log.example.com:514'
```

### Disable

```
- hosts: all
  roles:
    - role: syslogd
  vars:
    syslogd_state: 'disable'
    syslogd_server: 'tcp4://log.example.com:514'
```

### Remove

```
- hosts: all
  roles:
    - role: syslogd
  vars:
    syslogd_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: syslogd
  vars:
    syslogd_state: 'inactive'
```

## Parameters

### Role

`syslogd_state`

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

`syslogd_monitor_monit_state`

    Description: Control the 'syslogd_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`syslogd_pf_filters`

    Description: Define the 'syslogd_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass in inet proto { tcp, udp } from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 514 # syslog from internal private addresses
      pass in inet6 proto { tcp, udp } from fc00::/7 to port 514 # syslog from unique local addresses
      pass out inet proto { tcp, udp } to { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } port 514 # syslog to internal private addresses
      pass out inet6 proto { tcp, udp } to fc00::/7 port 514 # syslog to unique local addresses
    Options    :
      Examples: |
        pass in inet proto { tcp, udp } from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 514 # syslog from internal private addresses
        pass out inet proto { tcp, udp } to { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } port 514 # syslog to internal private addresses

`syslogd_pf_state`

    Description: Control the 'syslogd_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`syslogd_role`

    Description: Set the 'syslogd_role' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'client'
    Options    :
      Client: 'client'

`syslogd_server`

    Description: Define the 'syslogd_server' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "tcp4://log.{{ansible_domain}}:514"
    Options    :
      Examples: 'tcp4://log.example.com:514' | 'tcp6://logs.example.com:514'
      None    : ''

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

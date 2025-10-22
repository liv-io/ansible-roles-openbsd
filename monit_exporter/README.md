# monit_exporter

## Description

monit_exporter periodically scrapes the monit status and provides its data via
HTTP to Prometheus.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: monit_exporter
  vars:
    monit_exporter_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: monit_exporter
  vars:
    monit_exporter_state: 'enable'
```

### Disable

```
- hosts: all
  roles:
    - role: monit_exporter
  vars:
    monit_exporter_state: 'disable'
```

### Remove

```
- hosts: all
  roles:
    - role: monit_exporter
  vars:
    monit_exporter_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: monit_exporter
  vars:
    monit_exporter_state: 'inactive'
```

## Parameters

### Role

`monit_exporter_state`

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

`monit_exporter_monitor_monit_state`

    Description: Control the 'monit_exporter_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`monit_exporter_pf_filters`

    Description: Define the 'monit_exporter_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass in inet proto tcp from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 9388 # monit_exporter from internal private addresses
      pass in inet6 proto tcp from fc00::/7 to port 9388 # monit_exporter from unique local addresses
    Options    :
      Examples: |
        pass in inet proto tcp from 10.0.0.0/8 to port 9388 # monit_exporter from internal-networks

`monit_exporter_pf_state`

    Description: Control the 'monit_exporter_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`monit_exporter_version`

    Description: Define the 'monit_exporter_version' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '0.2.3'
    Options    :
      Examples: '0.0.1' | '0.0.2'

## Conflicts

## Dependencies

### Archives

`monit_exporter`

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

    Version: 7.7
    Version: 7.8

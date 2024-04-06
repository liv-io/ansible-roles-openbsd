# rsyslog

## Description

Rsyslog is an enhanced, multi-threaded syslog daemon. It supports MySQL,
syslog/TCP, RFC 3195, permitted sender lists, filtering on any message part, and
fine grain output format control. It is compatible with stock sysklogd and can
be used as a drop-in replacement. Rsyslog is simple to set up, with advanced
features suitable for enterprise-class, encryption-protected syslog relay chains.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: rsyslog
  vars:
    rsyslog_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: rsyslog
  vars:
    rsyslog_state: 'enable'
```

### Disable

```
- hosts: all
  roles:
    - role: rsyslog
  vars:
    rsyslog_state: 'disable'
```

### Remove

```
- hosts: all
  roles:
    - role: rsyslog
  vars:
    rsyslog_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: rsyslog
  vars:
    rsyslog_state: 'inactive'
```

### Config

```
vars:
  rsyslog_config_all:
    - name: "httpd"
      comment: "Apache HTTPD"
      section: "input"
      config:
        - {type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}
        - {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}

    - name: nginx
      comment: Nginx
      section: input
      config:
        - {type: imfile, File: /var/www/logs/*_access.log, Tag: nginx, Severity: info, Facility: local6}
        - {type: imfile, File: /var/www/logs/*_error.log, Tag: nginx, Severity: info, Facility: local6}
```

## Parameters

### Role

`rsyslog_state`

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

`rsyslog_config_all`

    Description: Define the 'rsyslog_config_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: httpd, comment: Apache HTTPD, section: input, config: [{type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}, {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}]}]
      None    : []

`rsyslog_config_group`

    Description: Define the 'rsyslog_config_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: httpd, comment: Apache HTTPD, section: input, config: [{type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}, {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}]}]
      None    : []

`rsyslog_config_host`

    Description: Define the 'rsyslog_config_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: httpd, comment: Apache HTTPD, section: input, config: [{type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}, {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}]}]
      None    : []

`rsyslog_monitor_monit_state`

    Description: Control the 'rsyslog_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`rsyslog_pf_filters`

    Description: Define the 'rsyslog_pf_filters' option.
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
        pass in inet proto { tcp, udp } from 10.0.0.0/8 to port 514 # syslog from internal-networks
        pass out inet proto { tcp, udp } to 10.0.0.0/8 port 514 # syslog to internal-networks

`rsyslog_pf_state`

    Description: Control the 'rsyslog_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`rsyslog_role`

    Description: Set the 'rsyslog_role' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'client'
    Options    :
      Client: 'client'
      Server: 'server'

`rsyslog_server`

    Description: Define the 'rsyslog_server' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "log.{{ansible_domain}}"
    Options    :
      Examples: 'log.example.com' | 'logs.example.com'
      None    : ''

## Conflicts

## Dependencies

### Packages

`rsyslog`

    Version: >= 8.0
    Name   :
      OpenBSD 7.4: 'rsyslog'
      OpenBSD 7.5: 'rsyslog'

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

    Version: 7.4
    Version: 7.5

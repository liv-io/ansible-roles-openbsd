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

`rsyslog_config_all`

    Description: Define the 'rsyslog_config_all' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: httpd, comment: Apache HTTPD, section: input, config: [{type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}, {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}]}]
      None    : []

`rsyslog_config_group`

    Description: Define the 'rsyslog_config_group' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: httpd, comment: Apache HTTPD, section: input, config: [{type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}, {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}]}]
      None    : []

`rsyslog_config_host`

    Description: Define the 'rsyslog_config_host' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: httpd, comment: Apache HTTPD, section: input, config: [{type: imfile, File: /var/www/logs/*access_log, Tag: httpd, Severity: info, Facility: local6}, {type: imfile, File: /var/www/logs/*error_log, Tag: httpd, Severity: info, Facility: local6}]}]
      None    : []

`rsyslog_monitor_monit_state`

    Description: Control the 'rsyslog_monitor_monit_state' option.
    Implemented: 0.2.0
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`rsyslog_role`

    Description: Set the 'rsyslog_role' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'client'
    Options    :
      Client: 'client'
      Server: 'server'

`rsyslog_server`

    Description: Define the 'rsyslog_server' option.
    Implemented: 0.1.0
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
      OpenBSD 7.3: 'rsyslog'
      OpenBSD 7.4: 'rsyslog'

## Parameters

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

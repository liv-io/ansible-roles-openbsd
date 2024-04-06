# restic

## Description

Restic is a program that does backups right and was designed to be easy, fast
verifiable, secure and efficient.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: restic
  vars:
    restic_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: restic
  vars:
    restic_state: 'enable'
```

### Disable

```
- hosts: all
  roles:
    - role: restic
  vars:
    restic_state: 'disable'
```

### Remove

```
- hosts: all
  roles:
    - role: restic
  vars:
    restic_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: restic
  vars:
    restic_state: 'inactive'
```

## Parameters

### Role

`restic_state`

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

`restic_cacert`

    Description: Define the 'restic_cacert' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: '/etc/pki/file.crt' | '/etc/ssl/file.crt'
      None    : ''

`restic_exclude`

    Description: Define the 'restic_exclude' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['/data/restic', '/data/rest-server', '/tmp', '/var/tmp']
    Options    :
      Examples: ['/tmp', '/data/example/*.tmp']
      None    : []

`restic_http_proxy`

    Description: Define the 'restic_http_proxy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'http://proxy.domain.tld:3128'
      None    : ''

`restic_https_proxy`

    Description: Define the 'restic_https_proxy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'http://proxy.domain.tld:3128'
      None    : ''

`restic_include`

    Description: Define the 'restic_include' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['/app', '/backup', '/data', '/etc', '/home', '/opt', '/root', '/usr/local/etc', '/var/log', '/var/opt', '/var/www']
    Options    :
      Examples: ['/backup', '/data/example/*.data']
      None    : []

`restic_keep_daily`

    Description: Set the 'restic_keep_daily' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 7
    Options    :
      Examples: 1 | 2 | 3

`restic_keep_hourly`

    Description: Set the 'restic_keep_hourly' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 12
    Options    :
      Examples: 3 | 12 | 24

`restic_keep_monthly`

    Description: Set the 'restic_keep_monthly' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 3
    Options    :
      Examples: 1 | 2 | 3

`restic_keep_weekly`

    Description: Set the 'restic_keep_weekly' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 4
    Options    :
      Examples: 1 | 2 | 3

`restic_limit_download`

    Description: Set the 'restic_limit_download' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 0
    Options    :
      Examples: 0 | 1024 | 4096 | 8192

`restic_limit_upload`

    Description: Set the 'restic_limit_upload' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 0
    Options    :
      Examples: 0 | 1024 | 4096 | 8192

`restic_monitor_mail_from_address`

    Description: Define the 'restic_monitor_mail_from_address' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "root@{{ansible_domain}}"
    Options    :
      Examples: 'root@domain.tld' | 'admin@domain.tld' | 'user@domain.tld'

`restic_monitor_mail_to_address`

    Description: Define the 'restic_monitor_mail_to_address' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ["admin@{{ansible_domain}}"]
    Options    :
      Examples: ['root@domain.tld'] | ['root@domain.tld', 'admin@domain.tld']
                ['root@domain.tld', 'admin@domain.tld', 'user@domain.tld']

`restic_monitor_mail_state`

    Description: Control the 'restic_monitor_mail_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`restic_monitor_prom_state`

    Description: Control the 'restic_monitor_prom_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`restic_monitor_prom_textfile_collector`

    Description: Define the 'restic_monitor_prom_textfile_collector' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '/var/node_exporter/textfile_collector'
    Options    :
      Examples: '/var/node_exporter/textfile_collector'

`restic_password`

    Description: Define the 'restic_password' option.
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'qW.t_hvfFp9BHtFt-xsFqCq_42jwNDgs' | 'pLj6.us3u-CHMSd5FHV8oq28q3NKfn_i'

`restic_pf_filters`

    Description: Define the 'restic_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass out inet proto tcp to any port 443 # restic to any
      pass out inet6 proto tcp to any port 443 # restic to any
    Options    :
      Examples: |
        pass out inet proto tcp to 10.0.0.0/8 port 443 # restic to internal-networks

`restic_pf_state`

    Description: Control the 'restic_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`restic_repository_name`

    Description: Define the 'restic_repository_name' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "{{ansible_hostname}}"
    Options    :
      Examples: 'hostname' | 'pretty-name'

`restic_run_backup_day`

    Description: Define the 'restic_run_backup_day' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : '*'
    Options    :
      Examples: '1' | '*/2'

`restic_run_backup_hour`

    Description: Define the 'restic_run_backup_hour' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : '2'
    Options    :
      Examples: '5' | '*/6'

`restic_run_backup_minute`

    Description: Define the 'restic_run_backup_minute' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : "{{10|random(seed=inventory_hostname)}}"
    Options    :
      Examples: '42' | '*/30'

`restic_run_backup_month`

    Description: Define the 'restic_run_backup_month' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : '*'
    Options    :
      Examples: '10' | '*/1'

`restic_run_backup_weekday`

    Description: Define the 'restic_run_backup_weekday' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : '*'
    Options    :
      Examples: '6' | 'Saturday'

`restic_server_address`

    Description: Define the 'restic_server_address' option.
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'backup.domain.tld' | 'restic.domain.tld'

`restic_server_password`

    Description: Define the 'restic_server_password' option.
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'vHK.kQ9bsWrL4ePaDn_5' | 'm2wL.E57MdnrSgFSP_AC'

`restic_server_port`

    Description: Define the 'restic_server_port' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : '443'
    Options    :
      Examples: '443' | '8000'

`restic_server_username`

    Description: Define the 'restic_server_username' option.
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'restic' | 'backup'

## Conflicts

## Dependencies

### Packages

`restic`

    Version: >= 0.8.3
    Name   :
      OpenBSD 7.4: 'restic'
      OpenBSD 7.5: 'restic'

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

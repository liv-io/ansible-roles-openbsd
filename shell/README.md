# shell

## Description

The sh utility is the standard command interpreter for the system.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: shell
  vars:
    shell_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: shell
  vars:
    shell_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: shell
  vars:
    shell_state: 'inactive'
```

## Parameters

### Role

`shell_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

`shell_color_support`

    Description: Control the state of colored 'shell' commands.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`shell_ftp_proxy`

    Description: Define the 'shell_ftp_proxy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'ftp://proxy.domain.tld:3128'
      None    : ''

`shell_histsize`

    Description: Set the size of the 'shell' history variable.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '262144'
    Options    :
      Examples: '32768' | '65536' | '131072' | '262144'
      None    : ''

`shell_http_proxy`

    Description: Define the 'shell_http_proxy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'http://proxy.domain.tld:3128'
      None    : ''

`shell_https_proxy`

    Description: Define the 'shell_https_proxy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'http://proxy.domain.tld:3128'
      None    : ''

`shell_ls_time_style`

    Description: Define the time format of the 'ls' command.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '%Y-%m-%d %H:%M:%S'
    Options    :
      Examples: '%Y-%m-%d %H:%M:%S' | '+%Y-%m-%d %H:%M:%S'
      None    : ''

`shell_no_proxy`

    Description: Define the 'shell_no_proxy' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['localhost', '127.0.0.1', '::1']
    Options    :
      Examples: ['localhost', '127.0.0.1', '::1', 'example.org', 'example.com']
      None    : []

`shell_pager`

    Description: Define the default 'PAGER' variable.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : 'less'
    Options    :
      Examples: 'less' | 'more' | '/usr/bin/less' | '/usr/bin/more'
      None    : ''

`shell_safety`

    Description: Control the safety of various shell commands
                 (chmod, chown, ln, mv, rm...).
    Required   : False
    Value      : Predetermined

    Type       : Boolean
    Default    : True
    Options    : True | False

## Conflicts

## Dependencies

### Packages

`colorls`

    Version: >= 5.7
    Name   :
      OpenBSD 7.6: 'colorls'
      OpenBSD 7.7: 'colorls'

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

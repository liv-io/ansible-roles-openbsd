# package

## Description

Install or remove packages.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Inactive

```
- package: all
  roles:
    - role: package
  vars:
    package_state: 'inactive'
```

### Config

```
vars:
  package_config_all:
    - {name: 'apachetop', state: 'true'}
    - {name: 'arping', state: 'true'}
    - {name: 'colordiff', state: 'true'}
    - {name: 'colorls', state: 'true'}
    - {name: 'coreutils', state: 'true'}
    - {name: 'curl', state: 'true'}
    - {name: 'diffstat', state: 'true'}
    - {name: 'drill', state: 'true'}
    - {name: 'dsniff--no_x11', state: 'true'}
    - {name: 'echoping', state: 'true'}
    - {name: 'findutils', state: 'true'}
    - {name: 'fping', state: 'true'}
    - {name: 'git', state: 'true'}
    - {name: 'gawk', state: 'true'}
    - {name: 'gdiff', state: 'true'}
    - {name: 'ggrep', state: 'true'}
    - {name: 'gpatch', state: 'true'}
    - {name: 'gsed', state: 'true'}
    - {name: 'gtar--', state: 'true'}
    - {name: 'gnuwatch', state: 'true'}
    - {name: 'hping', state: 'true'}
    - {name: 'htop', state: 'true'}
    - {name: 'http_load', state: 'true'}
    - {name: 'http_ping', state: 'true'}
    - {name: 'icmpinfo', state: 'true'}
    - {name: 'ifstat--', state: 'true'}
    - {name: 'iftop', state: 'true'}
    - {name: 'iperf', state: 'true'}
    - {name: 'iperf3', state: 'true'}
    - {name: 'jq', state: 'true'}
    - {name: 'ldns-utils', state: 'true'}
    - {name: 'lftp', state: 'true'}
    - {name: 'lowdown', state: 'true'}
    - {name: 'moreutils', state: 'true'}
    - {name: 'mtr--', state: 'true'}
    - {name: 'multitail', state: 'true'}
    - {name: 'nano', state: 'true'}
    - {name: 'ncdu', state: 'true'}
    - {name: 'ngrep', state: 'true'}
    - {name: 'nload', state: 'true'}
    - {name: 'nmap', state: 'true'}
    - {name: 'nsping', state: 'true'}
    - {name: 'openssl', state: 'true'}
    - {name: 'patchutils', state: 'true'}
    - {name: 'pciutils', state: 'true'}
    - {name: 'pftop', state: 'true'}
    - {name: 'poink', state: 'true'}
    - {name: 'pv', state: 'true'}
    - {name: 'pwgen', state: 'true'}
    - {name: 'py3-jinja2', state: 'true'}
    - {name: 'py3-paramiko', state: 'true'}
    - {name: 'py3-yaml', state: 'true'}
    - {name: 'rsync--', state: 'true'}
    - {name: 'siege', state: 'true'}
    - {name: 'socat', state: 'true'}
    - {name: 'splint', state: 'true'}
    - {name: 'sshpass', state: 'true'}
    - {name: 'ssldump', state: 'true'}
    - {name: 'stress', state: 'true'}
    - {name: 'sysbench--', state: 'true'}
    - {name: 'tcpreplay', state: 'true'}
    - {name: 'unzip--', state: 'true'}
    - {name: 'usbutils', state: 'true'}
    - {name: 'wget', state: 'true'}
    - {name: 'zip', state: 'true'}

  package_config_group:
    - {name: 'minicom', state: 'true'}
    - {name: 'picocom', state: 'true'}

  package_config_host:
    - {name: 'nyancat', state: 'false'}
```

## Parameters

### Config

`state`

    Description: Control the package state.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'true'
    Options    :
      Install: 'true' | 'yes' | 'install'
      Remove : 'false' | 'no' | 'remove'

`name`

    Description: Define the package name.
    Implemented: 0.1.0
    Required   : True
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'htop' | 'nyancat'

### Role

`package_state`

    Description: Control the state of the role.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Inactive: 'quiesce' | 'inactive'

`package_config_all`

    Description: Define the 'package_config_all' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'colordiff', state: 'true'}, {name: 'curl', state: 'true'}, {name: 'ldns-utils', state: 'true'}, {name: 'htop', state: 'true'}, {name: 'jq', state: 'true'}, {name: 'wget', state: 'true'}]
      None    : []

`package_config_group`

    Description: Define the 'package_config_group' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'colordiff', state: 'true'}, {name: 'curl', state: 'true'}, {name: 'ldns-utils', state: 'true'}, {name: 'htop', state: 'true'}, {name: 'jq', state: 'true'}, {name: 'wget', state: 'true'}]
      None    : []

`package_config_host`

    Description: Define the 'package_config_host' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'colordiff', state: 'true'}, {name: 'curl', state: 'true'}, {name: 'ldns-utils', state: 'true'}, {name: 'htop', state: 'true'}, {name: 'jq', state: 'true'}, {name: 'wget', state: 'true'}]
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

    Version: 7.2
    Version: 7.3

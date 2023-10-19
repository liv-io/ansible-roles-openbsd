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
    - {name: 'apachetop', state: True}
    - {name: 'arping', state: True}
    - {name: 'colordiff', state: True}
    - {name: 'colorls', state: True}
    - {name: 'coreutils', state: True}
    - {name: 'curl', state: True}
    - {name: 'diffstat', state: True}
    - {name: 'drill', state: True}
    - {name: 'dsniff--no_x11', state: True}
    - {name: 'echoping', state: True}
    - {name: 'findutils', state: True}
    - {name: 'fping', state: True}
    - {name: 'git', state: True}
    - {name: 'gawk', state: True}
    - {name: 'gdiff', state: True}
    - {name: 'ggrep', state: True}
    - {name: 'gpatch', state: True}
    - {name: 'gsed', state: True}
    - {name: 'gtar--', state: True}
    - {name: 'gnuwatch', state: True}
    - {name: 'hping', state: True}
    - {name: 'htop', state: True}
    - {name: 'http_load', state: True}
    - {name: 'http_ping', state: True}
    - {name: 'icmpinfo', state: True}
    - {name: 'ifstat--', state: True}
    - {name: 'iftop', state: True}
    - {name: 'iperf', state: True}
    - {name: 'iperf3', state: True}
    - {name: 'jq', state: True}
    - {name: 'ldns-utils', state: True}
    - {name: 'lftp', state: True}
    - {name: 'lowdown', state: True}
    - {name: 'moreutils', state: True}
    - {name: 'mtr--', state: True}
    - {name: 'multitail', state: True}
    - {name: 'nano', state: True}
    - {name: 'ncdu', state: True}
    - {name: 'ngrep', state: True}
    - {name: 'nload', state: True}
    - {name: 'nmap', state: True}
    - {name: 'nsping', state: True}
    - {name: 'openssl', state: True}
    - {name: 'patchutils', state: True}
    - {name: 'pciutils', state: True}
    - {name: 'pftop', state: True}
    - {name: 'poink', state: True}
    - {name: 'pv', state: True}
    - {name: 'pwgen', state: True}
    - {name: 'py3-jinja2', state: True}
    - {name: 'py3-paramiko', state: True}
    - {name: 'py3-yaml', state: True}
    - {name: 'rsync--', state: True}
    - {name: 'siege', state: True}
    - {name: 'socat', state: True}
    - {name: 'splint', state: True}
    - {name: 'sshpass', state: True}
    - {name: 'ssldump', state: True}
    - {name: 'stress', state: True}
    - {name: 'sysbench--', state: True}
    - {name: 'tcpreplay', state: True}
    - {name: 'unzip--', state: True}
    - {name: 'usbutils', state: True}
    - {name: 'wget', state: True}
    - {name: 'zip', state: True}

  package_config_group:
    - {name: 'minicom', state: True}
    - {name: 'picocom', state: True}

  package_config_host:
    - {name: 'nyancat', state: False}
```

## Parameters

### Config

`state`

    Description: Control the package state.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

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
      Examples: [{name: 'colordiff', state: True}, {name: 'curl', state: True}, {name: 'ldns-utils', state: True}, {name: 'htop', state: True}, {name: 'jq', state: True}, {name: 'wget', state: True}]
      None    : []

`package_config_group`

    Description: Define the 'package_config_group' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'colordiff', state: True}, {name: 'curl', state: True}, {name: 'ldns-utils', state: True}, {name: 'htop', state: True}, {name: 'jq', state: True}, {name: 'wget', state: True}]
      None    : []

`package_config_host`

    Description: Define the 'package_config_host' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'colordiff', state: True}, {name: 'curl', state: True}, {name: 'ldns-utils', state: True}, {name: 'htop', state: True}, {name: 'jq', state: True}, {name: 'wget', state: True}]
      None    : []

## Conflicts

## Dependencies

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

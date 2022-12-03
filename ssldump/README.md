# ssldump

## Description

This program is an SSLv3/TLS network protocol analyzer. It identifies TCP
connections on the chosen network interface and attempts to interpret them as
SSLv3/TLS traffic. When ssldump identifies SSLv3/TLS traffic, ssldump decodes
the records and displays them in a textual form to stdout. And if provided with
the appropriate keying material, ssldump will also decrypt the connections and
display the application data traffic. This program is based on tcpdump,
a network monitoring and data acquisition tool.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: ssldump
  vars:
    ssldump_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: ssldump
  vars:
    ssldump_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: ssldump
  vars:
    ssldump_state: 'inactive'
```

## Parameters

### Role

`ssldump_state`

    Description: Control the state of the role.
    Implemented: 0.1.0
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

## Conflicts

## Dependencies

### Packages

`ssldump`

    Version: >= 0.9
    Name   :
      OpenBSD 7.1: 'ssldump'
      OpenBSD 7.2: 'ssldump'

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

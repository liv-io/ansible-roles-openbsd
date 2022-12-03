# tcpreplay

## Description

Tcpreplay is a tool to replay captured network traffic. Currently, tcpreplay
supports pcap (tcpdump) and snoop capture formats. Also included, is tcpprep a
tool to pre-process capture files to allow increased performance under certain
conditions as well as capinfo which provides basic information about capture
files.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: tcpreplay
  vars:
    tcpreplay_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: tcpreplay
  vars:
    tcpreplay_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: tcpreplay
  vars:
    tcpreplay_state: 'inactive'
```

## Parameters

### Role

`tcpreplay_state`

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

`tcpreplay`

    Version: >= 4.0
    Name   :
      OpenBSD 7.1: 'tcpreplay'
      OpenBSD 7.2: 'tcpreplay'

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

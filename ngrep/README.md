# ngrep

## Description

ngrep strives to provide most of GNU grep's common features, applying them to
the network layer. ngrep is a pcap-aware tool that will allow you to specify
extended regular or hexadecimal expressions to match against data payloads of
packets. It currently recognizes TCP, UDP, ICMP, IGMP and Raw protocols across
Ethernet, PPP, SLIP, FDDI, Token Ring, 802.11 and null interfaces, and
understands bpf filter logic in the same fashion as more common packet sniffing
tools, such as tcpdump and snoop.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: ngrep
  vars:
    ngrep_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: ngrep
  vars:
    ngrep_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: ngrep
  vars:
    ngrep_state: 'inactive'
```

## Parameters

### Role

`ngrep_state`

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

`ngrep`

    Version: >= 1.45
    Name   :
      OpenBSD 7.1: 'ngrep'
      OpenBSD 7.2: 'ngrep'

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

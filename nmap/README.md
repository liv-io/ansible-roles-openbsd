# nmap

## Description

Nmap is a utility for network exploration or security auditing. It supports ping
scanning (determine which hosts are up), many port scanning techniques
(determine what services the hosts are offering), and TCP/IP fingerprinting
(remote host operating system identification). Nmap also offers flexible target
and port specification, decoy scanning, determination of TCP sequence
predictability characteristics, reverse-identd scanning, and more. In addition
to the classic command-line nmap executable, the Nmap suite includes a flexible
data transfer, redirection, and debugging tool (netcat utility ncat), a utility
for comparing scan results (ndiff), and a packet generation and response
analysis tool (nping).

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: nmap
  vars:
    nmap_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: nmap
  vars:
    nmap_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: nmap
  vars:
    nmap_state: 'inactive'
```

## Parameters

### Role

`nmap_state`

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

`nmap`

    Version: >= 5.51
    Name   :
      OpenBSD 7.1: 'nmap'
      OpenBSD 7.2: 'nmap'

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

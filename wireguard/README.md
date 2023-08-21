# wireguard

## Description

WireGuard is a novel VPN that runs inside the Linux Kernel and uses
state-of-the-art cryptography (the "Noise" protocol). It aims to be faster,
simpler, leaner, and more useful than IPSec, while avoiding the massive
headache. It intends to be considerably more performant than OpenVPN. WireGuard
is designed as a general purpose VPN for running on embedded interfaces and
super computers alike, fit for many different circumstances. It runs over UDP.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: wireguard
  vars:
    wireguard_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: wireguard
  vars:
    wireguard_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: wireguard
  vars:
    wireguard_state: 'inactive'
```

### Config

```
vars:
  wireguard_config:
    - device: 'wg0'
      interfaces:
        - ip: '10.0.0.2'
          netmask: '255.255.255.0'
          description: "site-to-site vpn"
      listen_port: 51820
      private_key: 'yF0WEk5FcCquHWbYSt3wwuv6Bu6RBHWw+pfq21avd24='
      peers:
        - endpoint: '1.2.3.4:51820'
          public_key: 'RJquVUwxWCBBbM0puXnujeR3+X6L9Ttnm6e0LJ1Fgw4='
          description: 'site02.example.com'
          allowed_ips: ['10.0.0.12/32']
          persistent_keepalive: 25
        - endpoint: '5.6.7.8:51820'
          public_key: 'fmtMwFBFHz1i5KRk+uozBCSBtZzqy+NTRSjCGMd4exs='
          description: 'site03.example.com'
          allowed_ips: ['10.0.0.13/32']
          persistent_keepalive: 25
```

## Parameters

### Role

`wireguard_state`

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

`wireguard_config`

    Description: Define the 'wireguard_config' option.
    Implemented: 0.1.0
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{device: wg0, interfaces: [{ip: 10.0.0.2, netmask: 255.255.255.0, description: site-to-site vpn}], listen_port: 51820, private_key: yF0WEk5FcCquHWbYSt3wwuv6Bu6RBHWw+pfq21avd24=, peers: [{public_key: RJquVUwxWCBBbM0puXnujeR3+X6L9Ttnm6e0LJ1Fgw4=, description: site02.example.com, allowed_ips: [10.0.0.12/32], persistent_keepalive: 25}, {public_key: fmtMwFBFHz1i5KRk+uozBCSBtZzqy+NTRSjCGMd4exs=, description: site03.example.com, allowed_ips: [10.0.0.13/32], persistent_keepalive: 25}]}]
      None    : []

`wireguard_monitor_monit_state`

    Description: Control the 'wireguard_monitor_monit_state' option.
    Implemented: 0.2.0
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

## Conflicts

## Dependencies

### Packages

`wireguard-tools`

    Version: >= 1.0
    Name   :
      OpenBSD 7.2: 'wireguard-tools'
      OpenBSD 7.3: 'wireguard-tools'

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

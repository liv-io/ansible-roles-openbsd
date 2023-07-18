# wireguard

## Description

Nginx is a web server and a reverse proxy server for HTTP, SMTP, POP3 and IMAP
protocols, with a strong focus on high concurrency, performance and low memory
usage.

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
        - public_key: 'RJquVUwxWCBBbM0puXnujeR3+X6L9Ttnm6e0LJ1Fgw4='
          description: 'site02.example.com'
          allowed_ips: ['10.0.0.12/32']
          persistent_keepalive: 25
        - public_key: 'fmtMwFBFHz1i5KRk+uozBCSBtZzqy+NTRSjCGMd4exs='
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

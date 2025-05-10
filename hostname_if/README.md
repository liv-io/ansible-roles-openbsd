# hostname_if

## Description

The hostname.* files contain information regarding the configuration of each
network interface. One file should exist for each interface that is to be
configured, such as hostname.fxp0 or hostname.bridge0. A configuration file is
not needed for lo0.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: hostname
  vars:
    hostname_state: 'install'
    hostname_if_carp_allow: True
    hostname_if_carp_preempt: True
```

### Inactive

```
- hosts: all
  roles:
    - role: hostname
  vars:
    hostname_state: 'inactive'
```

### Config

```
vars:
  hostname_if_mygate:
    - '5.6.7.9'
    - '2001:bad:cafe::1'

  hostname_if_config_all: |

  # EXT

  - device: 'em0'
    link: up
    config: |
      description 'i_ext'

  - device: 'em1'
    link: up
    config:
      description 'i_ext'

  - device: 'aggr0'
    link: up
    config: |
      description 'i_ext'
      trunkport em0 trunkport em1 lacpmode active lacptimeout slow

  - device: 'carp1'
    link: up
    config: |
      description 'n_wan'
      inet6 2001:bad:cafe::11 64 vhid 255 carpdev aggr0 advskew 20 pass "Reng.eG,h.+,hCa6"

  - device: 'carp12'
    link: up
    config: |
      description 'n_wan'
      inet 5.6.7.12 255.255.255.248 NONE vhid 212 carpdev aggr0 advskew 20 pass "Jereb4e.ahWa-e6p"

  - device: 'carp13'
    link: up
    config: |
      description 'n_wan'
      inet 5.6.7.13 255.255.255.248 NONE vhid 213 carpdev aggr0 advskew 20 pass "Et.e4E,guSha.h.e"

  - device: 'carp14'
    link: up
    config: |
      description 'n_wan'
      inet 5.6.7.14 255.255.255.248 NONE vhid 214 carpdev aggr0 advskew 20 pass "V.p9baTh,hk,hpha"

  # INT

  - device: 'em2'
    link: up
    config: |
      description 'i_data'

  - device: 'em3'
    link: up
    config: |
      description 'i_data'

  - device: 'aggr1'
    link: up
    config: |
      description 'i_ext'
      trunkport em2 trunkport em3 lacpmode active lacptimeout slow

  # VLAN11 (mgmt)

  - device: 'vlan11'
    link: up
    config: |
      description 'i_mgmt'
      inet 10.1.11.2 255.255.255.0 NONE vnetid 11 vlandev aggr1
      inet6 2001:bad:cafe::11:2 112 vnetid 11 landev aggr1

  - device: 'carp411'
    link: up
    config: |
      description 'i_mgmt'
      inet 10.1.11.1 255.255.255.0 NONE vhid 11 carpdev vlan11 advskew 20 pass "Pha.hu2uph.el4,e"

  - device: 'carp611'
    link: up
    config: |
      description 'i_mgmt'
      inet6 2001:bad:cafe::11:1 112 vhid 111 carpdev vlan11 advskew 20 pass "EngAe2eej5V,ng8p"

  # VLAN12 (base)

  - device: 'vlan12'
    link: up
    config: |
      description 'i_base'
      inet 10.1.12.2 255.255.255.0 NONE vnetid 12 vlandev aggr1
      inet6 2001:bad:cafe::12:2 112 vnetid 12 landev aggr1

  - device: 'carp412'
    link: up
    config: |
      description 'i_base'
      inet 10.1.12.1 255.255.255.0 NONE vhid 12 carpdev vlan12 advskew 20 pass "2aHt54hs,Be.Nu.R"

  - device: 'carp612'
    link: up
    config: |
      description 'i_base'
      inet6 2001:bad:cafe::12:1 112 vhid 112 carpdev vlan12 advskew 20 pass "4hR7uj.j.ugh.ex5"

  # VLAN13 (dmz)

  - device: 'vlan13'
    link: up
    config: |
      description 'i_dmz'
      inet 10.1.13.2 255.255.255.0 NONE vnetid 13 vlandev aggr1
      inet6 2001:bad:cafe::13:2 112 vnetid 13 landev aggr1

  - device: 'carp413'
    link: up
    config: |
      description 'i_dmz'
      inet 10.1.13.1 255.255.255.0 NONE vhid 13 carpdev vlan13 advskew 20 pass "A.Vaet2C,fe.k,54"

  - device: 'carp613'
    link: up
    config: |
      description 'i_dmz'
      inet6 2001:bad:cafe::13:1 112 vhid 113 carpdev vlan13 advskew 20 pass "Ae+e9waPh5ga.Qu2"

  # VLAN14 (client)

  - device: 'vlan14'
    link: up
    config: |
      description 'i_dmz'
      inet 10.1.14.2 255.255.255.0 NONE vnetid 14 vlandev aggr1
      inet6 2001:bad:cafe::14:2 112 vnetid 14 landev aggr1

  - device: 'carp414'
    link: up
    config: |
      description 'i_dmz'
      inet 10.1.14.1 255.255.255.0 NONE vhid 14 carpdev vlan14 advskew 20 pass "Le3wTP.v5a.N2mu8"

  - device: 'carp614'
    link: up
    config: |
      description 'i_dmz'
      inet6 2001:bad:cafe::14:1 112 vhid 114 carpdev vlan14 advskew 20 pass "Ec4,h+a.She2ph,6"

  # SWITCH

  - device: 'em4'
    link: up
    config: |
      description 'i_switch'
      inet 10.1.1.2 255.255.255.0 NONE

  # PFSYNC

  - device: 'pfsync0'
    link: up
    config: |
      description 'pfsync'
      syncdev em5

  - device: 'em5'
    link: up
    config: |
      description 'i_pfsync'
      inet 10.1.0.2 255.255.255.0 NONE

## Parameters

### Role

`hostname_if_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'install'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Inactive: 'quiesce' | 'inactive'

`hostname_if_carp_allow`

    Description: Control the 'hostname_if_carp_allow' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`hostname_if_carp_preempt`

    Description: Control the 'hostname_if_carp_preempt' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`hostname_if_config_all`

    Description: Define the 'hostname_if_config_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples:
        - device: 'em0'
          link: up
          config: |
            description 'i_main'
            inet 10.1.12.10 255.255.255.0 NONE
      None    : []

`hostname_if_config_group`

    Description: Define the 'hostname_if_config_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples:
        - device: 'em0'
          link: up
          config: |
            description 'i_main'
            inet 10.1.12.10 255.255.255.0 NONE
      None    : []

`hostname_if_config_host`

    Description: Define the 'hostname_if_config_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples:
        - device: 'em0'
          link: up
          config: |
            description 'i_main'
            inet 10.1.12.10 255.255.255.0 NONE
      None    : []

`hostname_if_mygate`

    Description: Define the 'hostname_if_mygate' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ["{{ansible_default_ipv4.gateway|default('')}}", "{{ansible_default_ipv6.gateway|default('')}}"]
    Options    :
      Examples: ['5.6.7.9', '2001:bad:cafe::1']
      None    : []

## Conflicts

## Dependencies

### Roles

`sysctl`

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

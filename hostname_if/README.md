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
  hostname_if_config_all:
    - device: pfsync0
      interfaces:
        - { type: 'pfsync', syncdev: 'vio0', description: 'pfsync' }
    - device: vio0
      interfaces:
        - { ip: '10.1.1.10', netmask: '255.255.255.0', broadcast: '10.1.1.255', description: 'n_z_int_mgmt' }
      routes:
        - { network: 'default', gateway: '10.1.1.1' }
    - device: 'vio2'
      description: 'zone'
    - device: 'vlan300'
      interfaces:
        - { ip: '10.13.0.1', netmask: '255.255.255.0', vnetid: '300', vlandev: 'vio2', description: 'v_z_int_ca_base' }
    - device: 'carp300'
      interfaces:
        - { type: 'carp', ip: '10.13.0.1', netmask: '255.255.255.0', vhid: '3', carpdev: 'vlan300', advskew: '10', pass: 'yWk,jRcX.3X_wGT!9c59', description: 'v_z_int_ca_base' }

  hostname_if_config_group:
    - device: 'vio0'
      interfaces:
        - { ip: '10.1.1.10', netmask: '255.255.255.0', broadcast: '10.1.1.255', description: 'n_z_int_mgmt' }
      routes:
        - { network: 'default', gateway: '10.1.1.1' }
    - device: 'vio1'
      description: 'zone'
    - device: 'vlan301'
      interfaces:
        - { ip: '10.13.1.1', netmask: '255.255.255.0', vnetid: '301', vlandev: 'vio1', description: 'v_w_int_db' }

  hostname_if_config_host:
    - device: 'vio0'
      interfaces:
        - { ip: '10.1.1.10', netmask: '255.255.255.0', broadcast: '10.1.1.255', description: 'n_z_int_mgmt' }
      routes:
        - { network: 'default', gateway: '10.1.1.1' }
    - device: 'vio1'
      description: 'zone'
    - device: 'vlan301'
      interfaces:
        - { ip: '10.13.1.1', netmask: '255.255.255.0', vnetid: '301', vlandev: 'vio1', description: 'v_w_int_db' }
```

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
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{device: 'pfsync0', interfaces: [{type: 'pfsync', syncdev: 'vio0', description: 'pfsync'}]},
                 {device: 'vio0', interfaces: [{ip: '10.1.1.10', netmask: '255.255.255.0', broadcast: '10.1.1.255', description: 'n_z_int_mgmt'}],
                                     routes: [{network: 'default', gateway: '10.1.1.1'}]},
                 {device: 'vio1', description: 'transit'},
                 {device: 'vlan1000', interfaces: [{ip: '10.250.0.1', netmask: '255.255.255.0', vnetid: '100', vlandev: 'vio1', description: 'v_z_base_transit'}]},
                 {device: 'vlan1001', interfaces: [{ip: '10.250.1.1', netmask: '255.255.255.0', vnetid: '101', vlandev: 'vio1', description: 'v_z_prd_transit'}]},
                 {device: 'vio2', description: 'zone'},
                 {device: 'vlan300', interfaces: [{ip: '10.13.0.1', netmask: '255.255.255.0', vnetid: '300', vlandev: 'vio2', description: 'v_z_int_ca_base'}]},
                 {device: 'carp300', interfaces: [{type: 'carp', ip: '10.13.0.1', netmask: '255.255.255.0', vhid: '3', carpdev: 'vlan300', advskew: '10', pass: 'yWk,jRcX.3X_wGT!9c59', description: 'v_z_int_ca_base'}]},
                 {device: 'vlan301', interfaces: [{ip: '10.13.1.1', netmask: '255.255.255.0', vnetid: '301', vlandev: 'vio2', description: 'v_w_int_db'}]},
                 {device: 'vlan302', interfaces: [{ip: '10.13.2.1', netmask: '255.255.255.0', vnetid: '302', vlandev: 'vio2', description: 'v_w_int_app'}]}]
      None    : []

`hostname_if_config_group`

    Description: Define the 'hostname_if_config_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{device: 'pfsync0', interfaces: [{type: 'pfsync', syncdev: 'vio0', description: 'pfsync'}]},
                 {device: 'vio0', interfaces: [{ip: '10.1.1.10', netmask: '255.255.255.0', broadcast: '10.1.1.255', description: 'n_z_int_mgmt'}],
                                     routes: [{network: 'default', gateway: '10.1.1.1'}]},
                 {device: 'vio1', description: 'transit'},
                 {device: 'vlan1000', interfaces: [{ip: '10.250.0.1', netmask: '255.255.255.0', vnetid: '100', vlandev: 'vio1', description: 'v_z_base_transit'}]},
                 {device: 'vlan1001', interfaces: [{ip: '10.250.1.1', netmask: '255.255.255.0', vnetid: '101', vlandev: 'vio1', description: 'v_z_prd_transit'}]},
                 {device: 'vio2', description: 'zone'},
                 {device: 'vlan300', interfaces: [{ip: '10.13.0.1', netmask: '255.255.255.0', vnetid: '300', vlandev: 'vio2', description: 'v_z_int_ca_base'}]},
                 {device: 'carp300', interfaces: [{type: 'carp', ip: '10.13.0.1', netmask: '255.255.255.0', vhid: '3', carpdev: 'vlan300', advskew: '10', pass: 'yWk,jRcX.3X_wGT!9c59', description: 'v_z_int_ca_base'}]},
                 {device: 'vlan301', interfaces: [{ip: '10.13.1.1', netmask: '255.255.255.0', vnetid: '301', vlandev: 'vio2', description: 'v_w_int_db'}]},
                 {device: 'vlan302', interfaces: [{ip: '10.13.2.1', netmask: '255.255.255.0', vnetid: '302', vlandev: 'vio2', description: 'v_w_int_app'}]}]
      None    : []

`hostname_if_config_host`

    Description: Define the 'hostname_if_config_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{device: 'pfsync0', interfaces: [{type: 'pfsync', syncdev: 'vio0', description: 'pfsync'}]},
                 {device: 'vio0', interfaces: [{ip: '10.1.1.10', netmask: '255.255.255.0', broadcast: '10.1.1.255', description: 'n_z_int_mgmt'}],
                                     routes: [{network: 'default', gateway: '10.1.1.1'}]},
                 {device: 'vio1', description: 'transit'},
                 {device: 'vlan1000', interfaces: [{ip: '10.250.0.1', netmask: '255.255.255.0', vnetid: '100', vlandev: 'vio1', description: 'v_z_base_transit'}]},
                 {device: 'vlan1001', interfaces: [{ip: '10.250.1.1', netmask: '255.255.255.0', vnetid: '101', vlandev: 'vio1', description: 'v_z_prd_transit'}]},
                 {device: 'vio2', description: 'zone'},
                 {device: 'vlan300', interfaces: [{ip: '10.13.0.1', netmask: '255.255.255.0', vnetid: '300', vlandev: 'vio2', description: 'v_z_int_ca_base'}]},
                 {device: 'carp300', interfaces: [{type: 'carp', ip: '10.13.0.1', netmask: '255.255.255.0', vhid: '3', carpdev: 'vlan300', advskew: '10', pass: 'yWk,jRcX.3X_wGT!9c59', description: 'v_z_int_ca_base'}]},
                 {device: 'vlan301', interfaces: [{ip: '10.13.1.1', netmask: '255.255.255.0', vnetid: '301', vlandev: 'vio2', description: 'v_w_int_db'}]},
                 {device: 'vlan302', interfaces: [{ip: '10.13.2.1', netmask: '255.255.255.0', vnetid: '302', vlandev: 'vio2', description: 'v_w_int_app'}]}]
      None    : []

`hostname_if_mygate`

    Description: Define the 'hostname_if_mygate' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "{{ansible_default_ipv4.gateway}}"
    Options    :
      Examples: '1.1.1.1' | 10.1.1.1' | '192.168.1.1'
      Inactive: 'quiesce' | 'inactive'
      None    : ''

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

    Version: 7.3
    Version: 7.4

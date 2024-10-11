# tinc

## Description

tinc is a Virtual Private Network (VPN) daemon that uses tunnelling and
encryption to create a secure private network between hosts on the Internet.
Because the tunnel appears to the IP level network code as a normal network
device, there is no need to adapt any existing software. This tunnelling allows
VPN sites to share information with each other over the Internet without
exposing any information to others.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: tinc
  vars:
    tinc_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: tinc
  vars:
    tinc_state: 'enable'
    tinc_config:
      - name: 'dc_to_dc'
        state: True
        device: '/dev/tap0'
        process_priority: 'high'
        replay_window: '64'
        address: '10.0.0.1'
        netmask: '255.255.255.0'
        routes:
          - subnet: '10.20.0.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.20.1.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.20.2.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.30.0.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.30.1.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.30.2.0/24'
            gateway: '10.0.0.1'
        host: 'dc_1'
        connect_to: ['dc_2', 'dc_3']
        private_key: |
          -----BEGIN RSA PRIVATE KEY-----
          MIIJKAIBAAKCAgEA2aBBCsWsNZ0pSpWWlhc8ZHtKAnQUYsg/zBdQlnN0RR7Ts5VP
          ...
          ZCufWpPhCkasS9Lpoi9oMmVTbBSuApcDQVB9t84pS+MpIheBaLHLh/itDkE=
          -----END RSA PRIVATE KEY-----

        hosts:
          - name: 'dc_1'
            address: '1.1.1.1'
            port: 655
            subnets:
              - '10.0.0.1/32'
              - '10.10.0.0/24'
              - '10.10.1.0/24'
              - '10.10.2.0/24'
            public_key: |
              -----BEGIN RSA PUBLIC KEY-----
              MIICCgKCAgEA2aBBCsWsNZ0pSpWWlhc8ZHtKAnQUYsg/zBdQlnN0RR7Ts5VPu2bL
              ...
              bXwnczA7zumk8ueZfLrcgDLOIEN7W7oyPm6CFS8OF3BQ8NJR+RQSh48CAwEAAQ==
              -----END RSA PUBLIC KEY-----

          - name: 'dc_2'
            address: '2.2.2.2'
            port: 655
            subnets:
              - '10.0.0.2/32'
              - '10.20.0.0/24'
              - '10.20.1.0/24'
              - '10.20.2.0/24'
            public_key: |
              -----BEGIN RSA PUBLIC KEY-----
              MIICCgKCAgEA0PE1t/4LEyCVEkkiE7iEEmwkq9keXrNdsZqUS0gsjSjBeYNLjc2Y
              ...
              CTP9FbNDYozYT4z9IC5bKLf3rbdxejOes8WIOgmwM/t1k1sJ85+/rzMCAwEAAQ==
              -----END RSA PUBLIC KEY-----

          - name: 'dc_3'
            address: '3.3.3.3'
            port: 655
            subnets:
              - '10.0.0.3/32'
              - '10.30.0.0/24'
              - '10.30.1.0/24'
              - '10.30.2.0/24'
            public_key: |
              -----BEGIN RSA PUBLIC KEY-----
              MIICCgKCAgEA2vhYkBrbtKgMTnQWlL8MIMpAknW5wUfqW7MPVeyPiE32O1Mw9/P9
              ...
              qi4GFFuANidsSpiA0p1mxXGCEWucuoa4VYNuZbgPDbpdOciHd7BXqC0CAwEAAQ==
              -----END RSA PUBLIC KEY-----
```

### Disable

```
- hosts: all
  roles:
    - role: tinc
  vars:
    tinc_state: 'disable'
    tinc_config:
      - name: 'dc_to_dc'
        state: True
        device: '/dev/tap0'
        process_priority: 'high'
        replay_window: '64'
        address: '10.0.0.1'
        netmask: '255.255.255.0'
        routes:
          - subnet: '10.20.0.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.20.1.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.20.2.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.30.0.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.30.1.0/24'
            gateway: '10.0.0.1'
          - subnet: '10.30.2.0/24'
            gateway: '10.0.0.1'
        host: 'dc_1'
        connect_to: ['dc_2', 'dc_3']
        private_key: |
          -----BEGIN RSA PRIVATE KEY-----
          MIIJKAIBAAKCAgEA2aBBCsWsNZ0pSpWWlhc8ZHtKAnQUYsg/zBdQlnN0RR7Ts5VP
          ...
          ZCufWpPhCkasS9Lpoi9oMmVTbBSuApcDQVB9t84pS+MpIheBaLHLh/itDkE=
          -----END RSA PRIVATE KEY-----

        hosts:
          - name: 'dc_1'
            address: '1.1.1.1'
            port: 655
            subnets:
              - '10.0.0.1/32'
              - '10.10.0.0/24'
              - '10.10.1.0/24'
              - '10.10.2.0/24'
            public_key: |
              -----BEGIN RSA PUBLIC KEY-----
              MIICCgKCAgEA2aBBCsWsNZ0pSpWWlhc8ZHtKAnQUYsg/zBdQlnN0RR7Ts5VPu2bL
              ...
              bXwnczA7zumk8ueZfLrcgDLOIEN7W7oyPm6CFS8OF3BQ8NJR+RQSh48CAwEAAQ==
              -----END RSA PUBLIC KEY-----

          - name: 'dc_2'
            address: '2.2.2.2'
            port: 655
            subnets:
              - '10.0.0.2/32'
              - '10.20.0.0/24'
              - '10.20.1.0/24'
              - '10.20.2.0/24'
            public_key: |
              -----BEGIN RSA PUBLIC KEY-----
              MIICCgKCAgEA0PE1t/4LEyCVEkkiE7iEEmwkq9keXrNdsZqUS0gsjSjBeYNLjc2Y
              ...
              CTP9FbNDYozYT4z9IC5bKLf3rbdxejOes8WIOgmwM/t1k1sJ85+/rzMCAwEAAQ==
              -----END RSA PUBLIC KEY-----

          - name: 'dc_3'
            address: '3.3.3.3'
            port: 655
            subnets:
              - '10.0.0.3/32'
              - '10.30.0.0/24'
              - '10.30.1.0/24'
              - '10.30.2.0/24'
            public_key: |
              -----BEGIN RSA PUBLIC KEY-----
              MIICCgKCAgEA2vhYkBrbtKgMTnQWlL8MIMpAknW5wUfqW7MPVeyPiE32O1Mw9/P9
              ...
              qi4GFFuANidsSpiA0p1mxXGCEWucuoa4VYNuZbgPDbpdOciHd7BXqC0CAwEAAQ==
              -----END RSA PUBLIC KEY-----
```

### Remove

```
- hosts: all
  roles:
    - role: tinc
  vars:
    tinc_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: tinc
  vars:
    tinc_state: 'inactive'
```

## Parameters

### Role

`tinc_state`

    Description: Control the state of the role.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'enable'
    Options    :
      Install : 'true' | 'yes' | 'install'
      Enable  : 'start' | 'on' | 'enable'
      Disable : 'stop' | 'off' | 'disable'
      Remove  : 'false' | 'no' | 'remove'
      Inactive: 'quiesce' | 'inactive'

`tinc_config`

    Description: Define the 'tinc_config' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: [{name: 'dc_to_dc', state: True, address: '10.0.0.1', netmask: '255.255.255.0',
                  routes: [{subnet: '10.20.0.0/24', gateway: '10.0.0.1'}, subnet: '10.20.1.0/24', gateway: '10.0.0.1'},
                            subnet: '10.20.2.0/24', gateway: '10.0.0.1'}, subnet: '10.30.0.0/24', gateway: '10.0.0.1'},
                            subnet: '10.30.1.0/24', gateway: '10.0.0.1'}, subnet: '10.30.2.0/24', gateway: '10.0.0.1'}],
                  host: 'dc_1', connect_to: [ 'dc_2', 'dc_3'], private_key: '',
                  hosts: [{name: 'dc_1', address: '1.1.1.1', port: '655', subnets: ['10.0.0.1/32', '10.10.0.0/24', '10.10.1.0/24', '10.10.2.0/24'], public_key: ''},
                          {name: 'dc_2', address: '2.2.2.2', port: '655', subnets: ['10.0.0.2/32', '10.20.0.0/24', '10.20.1.0/24', '10.20.2.0/24'], public_key: ''},
                          {name: 'dc_3', address: '3.3.3.3', port: '655', subnets: ['10.0.0.3/32', '10.30.0.0/24', '10.30.1.0/24', '10.30.3.0/24'], public_key: ''}]}]
      None    : []

`tinc_monitor_monit_state`

    Description: Control the 'tinc_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`tinc_pf_filters`

    Description: Define the 'tinc_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass in inet proto { tcp, udp } from any to port 655 # tinc from any
      pass in inet6 proto { tcp, udp } from any to port 655 # tinc from any
      pass out inet proto { tcp, udp } to any port 655 # tinc to any
      pass out inet6 proto { tcp, udp } to any port 655 # tinc to any
    Options    :
      Examples: |
      pass in inet proto { tcp, udp } from any to port 655 # tinc from any
      pass out inet proto { tcp, udp } to any port 655 # tinc to any

`tinc_pf_state`

    Description: Control the 'tinc_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

## Conflicts

## Dependencies

### Packages

`tinc`

    Version: >= 1.0
    Name   :
      OpenBSD 7.5: 'tinc'
      OpenBSD 7.6: 'tinc'

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

    Version: 7.5
    Version: 7.6

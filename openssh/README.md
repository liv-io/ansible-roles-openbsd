# openssh

## Description

SSH (Secure SHell) is a program for logging into and executing commands on a
remote machine. SSH is intended to replace rlogin and rsh, and to provide secure
encrypted communications between two untrusted hosts over an insecure network.
X11 connections and arbitrary TCP/IP ports can also be forwarded over the secure
channel.
OpenSSH is OpenBSD's version of the last free version of SSH, bringing it up to
date in terms of security and features.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: openssh
  vars:
    openssh_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: openssh
  vars:
    openssh_state: 'enable'
    openssh_allow_users: ['user01', 'user02', 'user03']
    openssh_password_authentication: False
    openssh_listen_address: ['0.0.0.0']
```

### Disable

```
- hosts: all
  roles:
    - role: openssh
  vars:
    openssh_state: 'disable'
    openssh_allow_users: ['user01', 'user02', 'user03']
    openssh_password_authentication: False
    openssh_listen_address: ['0.0.0.0']
```

### Remove

```
- hosts: all
  roles:
    - role: openssh
  vars:
    openssh_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: openssh
  vars:
    openssh_state: 'inactive'
```

## Parameters

### Role

`openssh_state`

    Description: Control the state of the role.
                 'openssh' is a core service and should therefore not be
                 disabled.
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

`openssh_address_family`

    Description: Set the 'openssh_address_family' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'any'
    Options    :
      IPv4/IPv6: 'any' | 'all'
      IPv4     : 'inet' | 'ipv4'
      IPv6     : 'inet6' | 'ipv6'

`openssh_allow_groups`

    Description: Define the 'openssh_allow_groups' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: ['group1', 'group2', 'group3']
      None    : []

`openssh_allow_users`

    Description: Define the 'openssh_allow_users' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: ['user1', 'user2', 'user3']
      None    : []

`openssh_banner`

    Description: Control the 'openssh_banner' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_ciphers`

    Description: Define the 'openssh_ciphers' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['aes256-ctr', 'aes192-ctr']
    Options    :
      Examples: ['aes256-ctr']

`openssh_compression`

    Description: Control the 'openssh_compression' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_deny_groups`

    Description: Define the 'openssh_deny_groups' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: ['group1', 'group2', 'group3']
      None    : []

`openssh_deny_users`

    Description: Define the 'openssh_deny_users' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: ['user1', 'user2', 'user3']
      None    : []

`openssh_host_key`

    Description: Define the 'openssh_host_key' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['/etc/ssh/ssh_host_rsa_key', '/etc/ssh/ssh_host_ed25519_key']
    Options    :
      Examples: ['/etc/ssh/ssh_host_rsa_key']

`openssh_host_key_algorithms`

    Description: Define the 'openssh_host_key_algorithms' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['ssh-ed25519', 'ssh-rsa']
    Options    :
      Examples: ['ssh-ed25519']

`openssh_kex_algorithms`

    Description: Define the 'openssh_kex_algorithms' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['curve25519-sha256@libssh.org']
    Options    :
      Examples: ['curve25519-sha256']

`openssh_listen_address`

    Description: Define the 'openssh_listen_address' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['0.0.0.0']
    Options    :
      Examples: ['0.0.0.0'] | ['127.0.0.1', '::', '::1'] |
                ['192.168.1.1', '2001:0ec9:96b4:19e4:2421:9b3f:1480:8458']

`openssh_macs`

    Description: Define the 'openssh_macs' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['hmac-sha2-512', 'hmac-sha2-256']
    Options    :
      Examples: ['hmac-sha2-512']

`openssh_match`

    Description: Define the 'openssh_match' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'sftpuser', type: 'User', config: {'ChrootDirectory': '/opt/sftp', 'ForceCommand': 'internal-sftp'}},
                 {name: 'sftpgroup', type: 'Group', config: {'ChrootDirectory': '/opt/sftp', 'ForceCommand': 'internal-sftp'}}]
      None    : []

`openssh_monitor_monit_state`

    Description: Control the 'openssh_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openssh_password_authentication`

    Description: Control the 'openssh_password_authentication' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_permit_root_login`

    Description: Control the 'openssh_permit_root_login' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openssh_pf_filters`

    Description: Define the 'openssh_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass in inet proto tcp from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 22 # ssh from internal private addresses
      pass in inet6 proto tcp from fc00::/7 to port 22 # ssh from unique local addresses
    Options    :
      Examples: |
        pass in inet proto tcp from 10.0.0.0/8 to port 22 # ssh from internal-networks

`openssh_pf_state`

    Description: Control the 'openssh_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openssh_port`

    Description: Define the 'openssh_port' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array, Integer, String
    Default    : ['22']
    Options    :
      Examples: ['22'] | ['22', '222'] | ['22', '8022']

`openssh_print_motd`

    Description: Control the 'openssh_print_motd' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_print_last_log`

    Description: Control the 'openssh_print_last_log' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_pubkey_authentication`

    Description: Control the 'openssh_pubkey_authentication' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_rsa_authentication`

    Description: Control the 'openssh_rsa_authentication' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_tcp_keep_alive`

    Description: Control the 'openssh_tcp_keep_alive' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`openssh_use_dns`

    Description: Control the 'openssh_use_dns' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openssh_version_addendum`

    Description: Define the 'openssh_version_addendum' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : 'none'
    Options    :
      Examples: 'hostname' | 'Operating System'

`openssh_x11_display_offset`

    Description: Define the 'openssh_x11_display_offset' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer, String
    Default    : 22
    Options    :
      Examples: 10 | 15

`openssh_x11_forwarding`

    Description: Control the 'openssh_x11_forwarding' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`openssh_x11_use_localhost`

    Description: Control the 'openssh_x11_use_localhost' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

## Conflicts

## Dependencies

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

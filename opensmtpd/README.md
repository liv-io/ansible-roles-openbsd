# opensmtpd

## Description

OpenSMTPD is a FREE implementation of the server-side SMTP protocol as defined
by RFC 5321, with some additional standard extensions. It allows ordinary
machines to exchange e-mails with other systems speaking the SMTP protocol.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: opensmtpd
  vars:
    opensmtpd_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: opensmtpd
  vars:
    opensmtpd_state: 'enable'
    opensmtpd_action_all:
      - {config: {'action "local" mbox alias <aliases>'}, comment: 'Action: local'}
      - {config: {'action "relay" relay host smtp+tls://user01_auth@mail.domain.tld auth <secrets>'}, comment: 'Action: relay'}
    opensmtpd_root_mail_address: 'root@domain.tld'
    opensmtpd_secrets_all:
      - {label: 'user01_auth', username: 'user01', password: 'S6_SD6B,Ybwt+Np-GuGEh+.p-xUeLbH3', comment: 'user01 credentials'}
    opensmtpd_table_all:
      - {config: {'table aliases file:/etc/mail/aliases'}, comment: 'Table: aliases'}
      - {config: {'table secrets file:/etc/mail/secrets'}, comment: 'Table: secrets'}
```

### Disable

```
- hosts: all
  roles:
    - role: opensmtpd
  vars:
    opensmtpd_state: 'disable'
    opensmtpd_action_all:
      - {config: {'action "local" mbox alias <aliases>'}, comment: 'Action: local'}
      - {config: {'action "relay" relay host smtp+tls://user01_auth@mail.domain.tld auth <secrets>'}, comment: 'Action: relay'}
    opensmtpd_root_mail_address: 'root@domain.tld'
    opensmtpd_secrets_all:
      - {label: 'user01_auth', username: 'user01', password: 'S6_SD6B,Ybwt+Np-GuGEh+.p-xUeLbH3', comment: 'user01 credentials'}
    opensmtpd_table_all:
      - {config: {'table aliases file:/etc/mail/aliases'}, comment: 'Table: aliases'}
      - {config: {'table secrets file:/etc/mail/secrets'}, comment: 'Table: secrets'}
```

### Remove

```
- hosts: all
  roles:
    - role: opensmtpd
  vars:
    opensmtpd_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: opensmtpd
  vars:
    opensmtpd_state: 'inactive'
```

## Parameters

### Role

`opensmtpd_state`

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

`opensmtpd_action_all`

    Description: Define the 'opensmtpd_action_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{config: {'action "local" mbox alias <aliases>'}, comment: 'Action: local'},
                  {config: {'action "relay" relay host smtp://mail'}, comment: 'Action: relay'}]
    Options    :
      Examples: [{config: {'action "local" mbox alias <aliases>'}, comment: 'Action: local'},
                 {config: {'action "relay" relay host smtp://mail'}, comment: 'Action: relay'}]
      None    : []

`opensmtpd_action_group`

    Description: Define the 'opensmtpd_action_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'action "local" mbox alias <aliases>'}, comment: 'Action: local'},
                 {config: {'action "relay" relay host smtp://mail'}, comment: 'Action: relay'}]
      None    : []

`opensmtpd_action_host`

    Description: Define the 'opensmtpd_action_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'action "local" mbox alias <aliases>'}, comment: 'Action: local'},
                 {config: {'action "relay" relay host smtp://mail'}, comment: 'Action: relay'}]
      None    : []

`opensmtpd_listen_all`

    Description: Define the 'opensmtpd_listen_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{config: {'listen on lo0'}, comment: 'Listen: lo0'}]
    Options    :
      Examples: [{config: {'listen on lo0'}, comment: 'Listen: lo0'}]
      None    : []

`opensmtpd_listen_group`

    Description: Define the 'opensmtpd_listen_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'listen on lo0'}, comment: 'Listen: lo0'}]
      None    : []

`opensmtpd_listen_host`

    Description: Define the 'opensmtpd_listen_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'listen on lo0'}, comment: 'Listen: lo0'}]
      None    : []

`opensmtpd_match_all`

    Description: Define the 'opensmtpd_match_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{config: {'match for local action "local"'}, comment: 'Match: local'}
                  {config: {'match for any action "relay"'}, comment: 'Match: relay'}]
    Options    :
      Examples: [{config: {'match for local action "local"'}, comment: 'Match: local'}
                 {config: {'match for any action "relay"'}, comment: 'Match: relay'}]
      None    : []

`opensmtpd_match_group`

    Description: Define the 'opensmtpd_match_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'match for local action "local"'}, comment: 'Match: local'}
                 {config: {'match for any action "relay"'}, comment: 'Match: relay'}]
      None    : []

`opensmtpd_match_host`

    Description: Define the 'opensmtpd_match_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'match for local action "local"'}, comment: 'Match: local'}
                 {config: {'match for any action "relay"'}, comment: 'Match: relay'}]
      None    : []

`opensmtpd_monitor_monit_state`

    Description: Control the 'opensmtpd_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`opensmtpd_pf_filters`

    Description: Define the 'opensmtpd_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass in inet proto tcp from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 25 # smtp from internal private addresses
      pass in inet6 proto tcp from fc00::/7 to port 25 # smtp from unique local addresses
      pass out inet proto tcp to { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } port 25 # smtp to internal private addresses
      pass out inet6 proto tcp to fc00::/7 port 25 # smtp to unique local addresses
    Options    :
      Examples: |
        pass in inet proto tcp from 10.0.0.0/8 to port 25 # smtp from internal-networks
        pass out inet proto tcp to 10.0.0.0/8 port 25 # smtp to internal-networks

`opensmtpd_pf_state`

    Description: Control the 'opensmtpd_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`opensmtpd_root_mail_address`

    Description: Define the 'opensmtpd_root_mail_address' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "root@{{ansible_domain}}"
    Options    :
      Examples: 'root@domain.tld' | 'admin@domain.tld' | 'user@domain.tld'

`opensmtpd_secrets_all`

    Description: Define the 'opensmtpd_secrets_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{label: 'user01_auth', username: 'user01', password: 'S6_SD6B,Ybwt+Np-GuGEh+.p-xUeLbH3', comment: 'user01 credentials'},
                 {label: 'user02_auth', username: 'user02', password: 'bvU8tP6!MF9t+hudKa,nkjP,r-oKUfip', comment: 'user02 credentials'}]
      None    : []

`opensmtpd_secrets_group`

    Description: Define the 'opensmtpd_secrets_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{label: 'user01_auth', username: 'user01', password: 'S6_SD6B,Ybwt+Np-GuGEh+.p-xUeLbH3', comment: 'user01 credentials'},
                 {label: 'user02_auth', username: 'user02', password: 'bvU8tP6!MF9t+hudKa,nkjP,r-oKUfip', comment: 'user02 credentials'}]
      None    : []

`opensmtpd_secrets_host`

    Description: Define the 'opensmtpd_secrets_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{label: 'user01_auth', username: 'user01', password: 'S6_SD6B,Ybwt+Np-GuGEh+.p-xUeLbH3', comment: 'user01 credentials'},
                 {label: 'user02_auth', username: 'user02', password: 'bvU8tP6!MF9t+hudKa,nkjP,r-oKUfip', comment: 'user02 credentials'}]
      None    : []

`opensmtpd_table_all`

    Description: Define the 'opensmtpd_table_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{config: {'table aliases file:/etc/mail/aliases'}, comment: 'Table: aliases'},
                  {config: {'table secrets file:/etc/mail/secrets'}, comment: 'Table: secrets'}]
    Options    :
      Examples: [{config: {'table aliases file:/etc/mail/aliases'}, comment: 'Table: aliases'},
                 {config: {'table secrets file:/etc/mail/secrets'}, comment: 'Table: secrets'}]
      None    : []

`opensmtpd_table_group`

    Description: Define the 'opensmtpd_table_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'table aliases file:/etc/mail/aliases'}, comment: 'Table: aliases'},
                 {config: {'table secrets file:/etc/mail/secrets'}, comment: 'Table: secrets'}]
      None    : []

`opensmtpd_table_host`

    Description: Define the 'opensmtpd_table_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{config: {'table aliases file:/etc/mail/aliases'}, comment: 'Table: aliases'},
                 {config: {'table secrets file:/etc/mail/secrets'}, comment: 'Table: secrets'}]
      None    : []

## Conflicts

### Roles

`postfix`

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

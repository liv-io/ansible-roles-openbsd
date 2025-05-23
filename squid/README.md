# squid

## Description

Squid is a high-performance proxy caching server for Web clients, supporting
FTP, gopher, and HTTP data objects. Unlike traditional caching software, Squid
handles all requests in a single, non-blocking, I/O-driven process. Squid keeps
meta data and especially hot objects cached in RAM, caches DNS lookups, supports
non-blocking DNS lookups, and implements negative caching of failed requests.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: squid
  vars:
    squid_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: squid
  vars:
    squid_state: 'enable'
    squid_acl:
      - {name: 'src_network_base', type: 'src', value: '10.1.1.0/24', comment: 'n_base'}
    squid_http_access:
      - {action: 'allow', source: 'src_network_base', protocol: 'http', destination: 'dst_domain_allowed', comment: 'Allow 'n_base' to access allowed domains via http'}
      - {action: 'allow', source: 'src_network_base', protocol: 'https SSL_ports', destination: 'dst_domain_allowed', comment: 'Allow 'n_base' to access allowed domains via https'}
      - {action: 'allow', source: 'src_network_base', protocol: 'http', destination: 'dst_network_allowed', comment: 'Allow 'n_base' to access allowed networks via http'}
      - {action: 'allow', source: 'src_network_base', protocol: 'https SSL_ports', destination: 'dst_network_allowed', comment: 'Allow 'n_base' to access allowed networks via https'}
    squid_domain_allowed:
      - {name: 'ftp.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'ftp.eu.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'ftp2.eu.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'mirror.switch.ch', comment: 'OpenBSD: Updates'}
      - {name: 'cdn.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'stable.mtier.org', comment: 'OpenBSD: mtier Packages'}
```

### Disable

```
- hosts: all
  roles:
    - role: squid
  vars:
    squid_state: 'disable'
    squid_acl:
      - {name: 'src_network_base', type: 'src', value: '10.1.1.0/24', comment: 'n_base'}
    squid_http_access:
      - {action: 'allow', source: 'src_network_base', protocol: 'http', destination: 'dst_domain_allowed', comment: 'Allow 'n_base' to access allowed domains via http'}
      - {action: 'allow', source: 'src_network_base', protocol: 'https SSL_ports', destination: 'dst_domain_allowed', comment: 'Allow 'n_base' to access allowed domains via https'}
      - {action: 'allow', source: 'src_network_base', protocol: 'http', destination: 'dst_network_allowed', comment: 'Allow 'n_base' to access allowed networks via http'}
      - {action: 'allow', source: 'src_network_base', protocol: 'https SSL_ports', destination: 'dst_network_allowed', comment: 'Allow 'n_base' to access allowed networks via https'}
    squid_domain_allowed:
      - {name: 'ftp.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'ftp.eu.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'ftp2.eu.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'mirror.switch.ch', comment: 'OpenBSD: Updates'}
      - {name: 'cdn.openbsd.org', comment: 'OpenBSD: Updates'}
      - {name: 'stable.mtier.org', comment: 'OpenBSD: mtier Packages'}
```

### Remove

```
- hosts: all
  roles:
    - role: squid
  vars:
    squid_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: squid
  vars:
    squid_state: 'inactive'
```

## Parameters

### Role

`squid_state`

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

`squid_acl`

    Description: Define the 'squid_acl' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'src_network_base', type: 'src', value: '10.1.1.0/24', comment: 'n_base'},
                 {name: 'src_network_mgmt', type: 'src', value: '10.1.2.0/24', comment: 'n_mgmt'}]
      None    : []

`squid_acl_ssl_ports`

    Description: Define the 'squid_acl_ssl_ports' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['443']
    Options    :
      Examples: ['443', '8443']

`squid_cache_dir`

    Description: Define the 'squid_cache_dir' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{type: 'ufs', size: '8192', first_level: '16', second_level: '256'}]
    Options    :
      Examples: [{type: 'ufs', path: '/var/squid/cache', size: '2048', first_level: '16', second_level: '256'}]

`squid_cache_mem`

    Description: Define the 'squid_cache_mem' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '256 MB'
    Options    :
      Examples: '128 MB' | '256 MB' | '512 MB'

`squid_cache_mgr`

    Description: Define the 'squid_cache_mgr' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "admin@{{ansible_domain}}"
    Options    :
      Examples: 'admin@domain.tld' | 'root@domain.tld'

`squid_cache_replacement_policy`

    Description: Define the 'squid_cache_replacement_policy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : 'lru'
    Options    :
      Examples: 'lru' | 'heap GDSF' | 'heap LFUDA' | 'heap LRU'

`squid_cachemgr_passwd`

    Description: Define the 'squid_cachemgr_passwd' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{password: 'disable', action: 'all', comment: 'disable all actions'}]
    Options    :
      Examples: [{password: '75PdwS-urHrm4pV,Xc67hDr.4NwgWmv6', action: 'shutdown', comment: 'execute shutdown'},
                 {password: 'v6xQ,g5cL-mm.r4cb3,W', action: 'info stats/objects', comment: 'get info'}]
      None    : []

`squid_domain_allowed`

    Description: Define the 'squid_domain_allowed' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
                 {name: 'ftp.openbsd.org', comment: 'OpenBSD: Updates'},
                 {name: 'ftp.eu.openbsd.org', comment: 'OpenBSD: Updates'},
                 {name: 'ftp2.eu.openbsd.org', comment: 'OpenBSD: Updates'},
                 {name: 'mirror.switch.ch', comment: 'OpenBSD: Updates'},
                 {name: 'cdn.openbsd.org', comment: 'OpenBSD: Updates'},
                 {name: 'stable.mtier.org', comment: 'OpenBSD: mtier Packages'}]
      None    : []

`squid_domain_blocked`

    Description: Define the 'squid_domain_blocked' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: 'example.com', comment: 'example.com'},
                 {name: 'example.org', comment: 'example.org'}]
      None    : []

`squid_http_port`

    Description: Set the 'squid_http_port' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 3128
    Options    :
      Examples: 8080

`squid_http_access`

    Description: Define the 'squid_http_access' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{action: 'allow', source: 'src_network_rfc1918', protocol: 'http', destination: 'dst_domain_allowed', comment: 'Allow RFC 1918 networks to access allowed domains via http'},
                  {action: 'allow', source: 'src_network_rfc1918', protocol: 'https SSL_ports', destination: 'dst_domain_allowed', comment: 'Allow RFC 1918 networks to access allowed domains via https'},
                  {action: 'allow', source: 'src_network_rfc1918', protocol: 'http', destination: 'dst_network_allowed', comment: 'Allow RFC 1918 networks to access allowed networks via http'},
                  {action: 'allow', source: 'src_network_rfc1918', protocol: 'https SSL_ports', destination: 'dst_network_allowed', comment: 'Allow RFC 1918 networks to access allowed networks via https'},
                  {action: 'allow', source: 'src_network_unrestricted', protocol: 'http', destination: 'all', comment: 'Allow unrestricted hosts to access any resource via http'},
                  {action: 'allow', source: 'src_network_unrestricted', protocol: 'https SSL_ports', destination: 'all', comment: 'Allow unrestricted hosts to access any resource via https'}]
    Options    :
      Examples: [{action: 'allow', source: 'src_network_base', protocol: 'http', destination: 'dst_domain_allowed', comment: 'Allow 'n_base' to access allowed domains via http'},
                 {action: 'allow', source: 'src_network_base', protocol: 'https SSL_ports', destination: 'dst_domain_allowed', comment: 'Allow 'n_base' to access allowed domains via https'},
                 {action: 'allow', source: 'src_network_base', protocol: 'http', destination: 'dst_network_allowed', comment: 'Allow 'n_base' to access allowed networks via http'},
                 {action: 'allow', source: 'src_network_base', protocol: 'https SSL_ports', destination: 'dst_network_allowed', comment: 'Allow 'n_base' to access allowed networks via https'},
                 {action: 'allow', source: 'src_network_mgmt', protocol: 'http', destination: 'dst_domain_allowed', comment: 'Allow 'n_mgmt' to access allowed domains via http'},
                 {action: 'allow', source: 'src_network_mgmt', protocol: 'https SSL_ports', destination: 'dst_domain_allowed', comment: 'Allow 'n_mgmt' to access allowed domains via https'},
                 {action: 'allow', source: 'src_network_mgmt', protocol: 'http', destination: 'dst_network_allowed', comment: 'Allow 'n_mgmt' to access allowed networks via http'},
                 {action: 'allow', source: 'src_network_mgmt', protocol: 'https SSL_ports', destination: 'dst_network_allowed', comment: 'Allow 'n_mgmt' to access allowed networks via https'}]
      None    : []

`squid_httpd_suppress_version_string`

    Description: Control the 'squid_httpd_suppress_version_string' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`squid_mail_from`

    Description: Define the 'squid_mail_from' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "admin@{{ansible_domain}}"
    Options    :
      Examples: 'admin@domain.tld' | 'squid@domain.tld'
      None    : ''

`squid_max_filedescriptors`

    Description: Set the 'squid_max_filedescriptors' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 4096
    Options    :
      Examples: 2048 | 4096 | 8192

`squid_maximum_object_size`

    Description: Define the 'squid_maximum_object_size' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '262144 KB'
    Options    :
      Examples: '4096 KB' | '65536 KB' | '131072 KB'

`squid_maximum_object_size_in_memory`

    Description: Define the 'squid_maximum_object_size_in_memory' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '2048 KB'
    Options    :
      Examples: '512 KB' | '1024 KB' | '4096 KB'

`squid_memory_replacement_policy`

    Description: Define the 'squid_memory_replacement_policy' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : 'lru'
    Options    :
      Examples: 'lru' | 'heap GDSF' | 'heap LFUDA' | 'heap LRU'

`squid_minimum_object_size`

    Description: Define the 'squid_minimum_object_size' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '0 KB'
    Options    :
      Examples: '128 KB' | '256 KB' | '512 KB'

`squid_monitor_monit_state`

    Description: Control the 'squid_monitor_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`squid_network_allowed`

    Description: Define the 'squid_network_allowed' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: '10.1.3.0/24', comment: 'n_web'},
                 {name: '10.1.4.0/24', comment: 'n_dmz'}]
      None    : []

`squid_network_blocked`

    Description: Define the 'squid_network_blocked' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : [{name: '10.0.0.0/8', comment: 'Deny proxy access to RFC 1918 networks'},
                  {name: '172.16.0.0/12', comment: 'Deny proxy access to RFC 1918 networks'},
                  {name: '192.168.0.0/16', comment: 'Deny proxy access to RFC 1918 networks'}]
    Options    :
      Examples: [{name: '10.1.1.0/24', comment: 'n_base'},
                 {name: '10.1.2.0/24', comment: 'n_mgmt'}]
      None    : []

`squid_network_unrestricted`

    Description: Define the 'squid_network_unrestricted' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array/Hash
    Default    : []
    Options    :
      Examples: [{name: '10.1.1.11', comment: 'mirror'},
                 {name: '10.1.1.12', comment: 'registry'}]
      None    : []

`squid_pf_filters`

    Description: Define the 'squid_pf_filters' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      pass in inet proto tcp from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 3128 # squid from internal private addresses
      pass in inet6 proto tcp from fc00::/7 to port 3128 # squid from unique local addresses
      pass out inet proto tcp to any port { 80, 443 } # http, https to any
      pass out inet6 proto tcp to any port { 80, 443 } # http, https to any
    Options    :
      Examples: |
      pass in inet proto tcp from 10.0.0.0/8 to port 3128 # squid from internal-networks
      pass out inet proto tcp to any port { 80, 443 } # http, https to any

`squid_pf_state`

    Description: Control the 'squid_pf_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
    Options    : True | False

`squid_quick_abort_max`

    Description: Define the 'squid_quick_abort_max' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '0 KB'
    Options    :
      Examples: '-1 KB' | '0 KB' | '128 KB'

`squid_quick_abort_min`

    Description: Define the 'squid_quick_abort_min' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '0 KB'
    Options    :
      Examples: '-1 KB' | '0 KB' | '128 KB'

`squid_shutdown_lifetime`

    Description: Set the 'squid_shutdown_lifetime' option.
    Required   : False
    Value      : Arbitrary
    Type       : Integer
    Default    : 1
    Options    :
      Examples: 10 | 20 | 30

`squid_visible_hostname`

    Description: Define the 'squid_visible_hostname' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : "{{ansible_hostname}}"
    Options    :
      Examples: 'squid' | 'forward-proxy'
      None    : ''

## Conflicts

## Dependencies

### Packages

`squid`

    Version: >= 3.5
    Name   :
      OpenBSD 7.6: 'squid'
      OpenBSD 7.7: 'squid'

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

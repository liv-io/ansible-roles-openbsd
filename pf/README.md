# pf

## Description

PF (Packet Filter) is a BSD licensed stateful packet filter, a central piece of
software for firewalling. PF is developed on OpenBSD, but has been ported to
many other operating systems including FreeBSD, NetBSD, DragonFly BSD and
Mac OS X.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: pf
  vars:
    pf_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: pf
  vars:
    pf_state: 'enable'
```

### Disable

```
- hosts: all
  roles:
    - role: pf
  vars:
   pf_state: 'disable'
```

### Remove

```
- hosts: all
  roles:
    - role: pf
  vars:
    pf_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: pf
  vars:
    pf_state: 'inactive'
```

### Config

```
vars:
  pf_filters_all: |
    # IPv4 ingress
    pass in inet proto tcp from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 22 # ssh from internal private addresses
    pass in inet proto tcp from 10.1.1.13 to port 9100 # node_exporter from monitoring-server
    pass in inet proto tcp from 10.1.1.13 to port 9115 # blackbox_exporter from monitoring-server
    pass in inet proto tcp from 10.1.1.13 to port 9388 # monit_exporter from monitoring-server
    # IPv4 egress
    pass out inet proto { tcp, udp } to 10.1.1.10 port 53 # dns to dns-server
    pass out inet proto udp to 10.1.1.11 port 123 # ntp to ntp-server
    pass out inet proto tcp to 10.1.1.15 port 443 # https to rest-server
    pass out inet proto tcp to 10.1.1.14 port 514 # syslog to logging-server
    pass out inet proto tcp to 10.1.1.12 port 3128 # squid to forward-proxy
  pf_filters_group: |
    pass in inet proto tcp from any to port { 80, 443 } # http, https from any
    pass out inet proto tcp to { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } port { 80, 443 } # http, https to internal private addresses
  pf_queues_all: |
    # vio0
    queue root_data on vio0 bandwidth 1G
    queue ssh parent root_data bandwidth 5M min 1M max 100M
    queue http parent root_data bandwidth 10M max 400M
    queue other parent root_data bandwidth 50M max 500M default
```

## Parameters

### Role

`pf_state`

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

`pf_filters_default`

    Description: Define the 'pf_filters_default' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      # IPv4 ingress
      pass in inet proto icmp icmp-type echorep # echo reply
      pass in inet proto icmp icmp-type unreach # destination unreachable
      pass in inet proto icmp icmp-type squench # packet loss, slow down
      pass in inet proto icmp icmp-type echoreq # echo request
      pass in inet proto icmp icmp-type timex # time exceeded
      pass in inet proto icmp icmp-type paramprob # invalid IP header
      # IPv6 ingress
      pass in inet6 proto icmp6 icmp6-type unreach # destination unreachable
      pass in inet6 proto icmp6 icmp6-type toobig # packet too big
      pass in inet6 proto icmp6 icmp6-type timex # time exceeded
      pass in inet6 proto icmp6 icmp6-type paramprob # invalid ipv6 header
      pass in inet6 proto icmp6 icmp6-type echoreq # echo service request
      pass in inet6 proto icmp6 icmp6-type echorep # echo service reply
      pass in inet6 proto icmp6 icmp6-type routeradv # router advertisement
      pass in inet6 proto icmp6 icmp6-type neighbrsol # neighbor solicitation
      pass in inet6 proto icmp6 icmp6-type neighbradv # neighbor advertisement
      # IPv4 egress
      pass out inet proto icmp icmp-type echorep # echo reply
      pass out inet proto icmp icmp-type unreach # destination unreachable
      pass out inet proto icmp icmp-type squench # packet loss, slow down
      pass out inet proto icmp icmp-type echoreq # echo request
      pass out inet proto icmp icmp-type timex # time exceeded
      pass out inet proto icmp icmp-type paramprob # invalid IP header
      # IPv6 egress
      pass out inet6 proto icmp6 icmp6-type unreach # destination unreachable
      pass out inet6 proto icmp6 icmp6-type toobig # packet too big
      pass out inet6 proto icmp6 icmp6-type timex # time exceeded
      pass out inet6 proto icmp6 icmp6-type paramprob # invalid ipv6 header
      pass out inet6 proto icmp6 icmp6-type echoreq # echo service request
      pass out inet6 proto icmp6 icmp6-type echorep # echo service reply
      pass out inet6 proto icmp6 icmp6-type routersol # router solicitation
      pass out inet6 proto icmp6 icmp6-type neighbrsol # neighbor solicitation
      pass out inet6 proto icmp6 icmp6-type neighbradv # neighbor advertisement
    Options    :
      Examples: |
        # IPv4 ingress
        pass in inet proto icmp icmp-type echorep # echo reply
        pass in inet proto icmp icmp-type echoreq # echo request
        # IPv4 egress
        pass out inet proto icmp icmp-type echorep # echo reply
        pass out inet proto icmp icmp-type echoreq # echo request
      None    : ''

`pf_filters_all`

    Description: Define the 'pf_filters_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      # IPv4 ingress
      pass in inet proto tcp from any to port 22 # ssh from any
      # IPv6 ingress
      pass in inet6 proto tcp from any to port 22 # ssh from any
      # IPv4 egress
      pass out inet proto { tcp, udp } to any port 53 # dns to any
      pass out inet proto udp to any port 123 # ntp to any
      pass out inet proto tcp to any port { 80, 443 } # http, https to any
      # IPv6 egress
      pass out inet6 proto { tcp, udp } to any port 53 # dns to any
      pass out inet6 proto udp to any port 123 # ntp to any
      pass out inet6 proto tcp to any port { 80, 443 } # http, https to any
    Options    :
      Examples: |
        # IPv4 ingress
        pass in inet proto tcp from { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } to port 22 # ssh from internal private addresses
        pass in inet proto tcp from 10.1.1.13 to port 9100 # node_exporter from monitoring-server
        pass in inet proto tcp from 10.1.1.13 to port 9115 # blackbox_exporter from monitoring-server
        pass in inet proto tcp from 10.1.1.13 to port 9388 # monit_exporter from monitoring-server
        # IPv4 egress
        pass out inet proto { tcp, udp } to 10.1.1.10 port 53 # dns to dns-server
        pass out inet proto udp to 10.1.1.11 port 123 # ntp to ntp-server
        pass out inet proto tcp to 10.1.1.15 port 443 # https to rest-server
        pass out inet proto tcp to 10.1.1.14 port 514 # syslog to logging-server
        pass out inet proto tcp to 10.1.1.12 port 3128 # squid to forward-proxy
      None    : ''

`pf_filters_group`

    Description: Define the 'pf_filters_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        pass in inet proto tcp from any to port { 80, 443 } # http, https from any
        pass out inet proto tcp to { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } port { 80, 443 } # http, https to internal private addresses
      None    : ''

`pf_filters_host`

    Description: Define the 'pf_filters_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        pass in inet proto tcp from any to port { 80, 443 } # http, https from any
        pass out inet proto tcp to { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 } port { 80, 443 } # http, https to internal private addresses
      None    : ''

`pf_filters_policies`

    Description: Define the 'pf_filters_policies' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      # default incoming policy
      block in log all
      # default outgoing policy
      block out all
    Options    :
      Examples: |
        # default incoming policy
        block in log all
        # default outgoing policy
        pass out log all

`pf_macros_default`

    Description: Define the 'pf_macros_default' option.
                 The flags 'S/SA' are safe when using scrubbing.
                 Use the flags 'S/SFRA' when scrubbing is disabled.
    Required   : False
    Value      : Arbitrary
    Type       : Hash
    Default    : {default_tcp: flags S/SA modulate state, default_udp: keep state}
    Options    :
      Examples:
        default_tcp: flags S/SFRA modulate state
        default_udp: keep state
      None: {}

`pf_macros_all`

    Description: Define the 'pf_macros_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : Hash
    Default    : {}
    Options    :
      Examples:
        dns_server: 10.1.1.10
        ntp_server: 10.1.1.11
        forward_proxy: 10.1.1.12
        monitoring_server: 10.1.1.13
        logging_server: 10.1.1.14
        rest_server: 10.1.1.15
      None: {}

`pf_macros_group`

    Description: Define the 'pf_macros_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : Hash
    Default    : {}
    Options    :
      Examples:
        dns_server: 10.1.1.10
        ntp_server: 10.1.1.11
        forward_proxy: 10.1.1.12
        monitoring_server: 10.1.1.13
        logging_server: 10.1.1.14
        rest_server: 10.1.1.15
      None: {}

`pf_macros_host`

    Description: Define the 'pf_macros_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : Hash
    Default    : {}
    Options    :
      Examples:
        dns_server: 10.1.1.10
        ntp_server: 10.1.1.11
        forward_proxy: 10.1.1.12
        monitoring_server: 10.1.1.13
        logging_server: 10.1.1.14
        rest_server: 10.1.1.15
      None: {}

`pf_normalization_scrub`

    Description: Define the 'pf_normalization_scrub' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      # scrub incoming traffic
      match in from any to any scrub (reassemble tcp)
      # scrub outgoing traffic
      match out from any to any scrub (random-id, reassemble tcp)
    Options    :
      Examples: |
        # scrub incoming traffic
        match in from any to any scrub (reassemble tcp)
        # scrub outgoing traffic
        match out from any to any scrub (random-id, reassemble tcp)
      None: ''

`pf_options_block_policy`

    Description: Control the 'pf_options_block_policy' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'drop'
    Options    :
      Return: 'return'
      Block : 'block'
      Drop  : 'drop'

`pf_options_debug`

    Description: Control the 'pf_options_debug' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'crit'
    Options    :
      Emergency    : 'emerg'
      Alert        : 'alert'
      Critical     : 'crit'
      Error        : 'err'
      Warning      : 'warning'
      Notice       : 'notice'
      Informational: 'info'
      Debug        : 'debug'

`pf_options_fingerprints`

    Description: Define the 'pf_options_fingerprints' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : '/etc/pf.os'
    Options    :
      Examples: '/etc/pf.os' | '/etc/pf.os-fingerprints'

`pf_options_hostid`

    Description: Define the 'pf_options_hostid' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: '1' | '2' | '3'
      None    : ''

`pf_options_limits`

    Description: Define the 'pf_options_limits' option.
    Required   : False
    Value      : Arbitrary
    Type       : Hash
    Default    : {}
    Options    :
      Examples:
        states: 20000
        frags: 20000
        src-nodes: 2000
        tables: 1000
        table-entries: 100000
      None    : {}

`pf_options_loginterface`

    Description: Define the 'pf_options_loginterface' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: 'em0' | 'ed1' | 'wlan2'
      None    : ''

`pf_options_optimization`

    Description: Control the 'pf_options_optimization' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'normal'
    Options    :
      Normal      : 'normal'
      High-Latency: 'high-latency'
      Satellite   : 'satellite'
      Aggressive  : 'aggressive'
      Conservative: 'conservative'

`pf_options_reassemble`

    Description: Control the 'pf_options_reassemble' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : True
    Options    : True | False

`pf_options_ruleset_optimization`

    Description: Control the 'pf_options_ruleset_optimization' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'basic'
    Options    :
      Basic  : 'basic'
      Profile: 'profile'
      None   : ''

`pf_options_skip`

    Description: Define the 'pf_options_skip' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : ['lo']
    Options    :
      Examples: ['lo'] | ['lo', 'em0']
      None    : []

`pf_options_state_defaults`

    Description: Define the 'pf_options_state_defaults' option.
    Required   : False
    Value      : Arbitrary
    Type       : Array
    Default    : []
    Options    :
      Examples: ['pflow', 'no-sync']
      None    : []

`pf_options_state_policy`

    Description: Control the 'pf_options_state_policy' option.
    Required   : False
    Value      : Predetermined
    Type       : String
    Default    : 'floating'
    Options    :
      Floating: 'floating'
      If-Bound: 'if-bound'

`pf_options_timeouts`

    Description: Define the 'pf_options_timeouts' option.
    Required   : False
    Value      : Arbitrary
    Type       : Hash
    Default    : {}
    Options    :
      Examples:
        tcp.first: 120
        tcp.established: 86400
        adaptive.start: 6000
        adaptive.end: 12000
      None    : {}

`pf_queues_default`

    Description: Define the 'pf_queues_default' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # vio0
        queue root_data on vio0 bandwidth 1G
        queue ssh parent root_data bandwidth 5M min 1M max 100M
        queue http parent root_data bandwidth 10M max 400M
        queue other parent root_data bandwidth 50M max 500M default
      None    : ''

`pf_queues_all`

    Description: Define the 'pf_queues_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # vio0
        queue root_data on vio0 bandwidth 1G
        queue ssh parent root_data bandwidth 5M min 1M max 100M
        queue http parent root_data bandwidth 10M max 400M
        queue other parent root_data bandwidth 50M max 500M default
      None    : ''

`pf_queues_group`

    Description: Define the 'pf_queues_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # vio0
        queue root_data on vio0 bandwidth 1G
        queue ssh parent root_data bandwidth 5M min 1M max 100M
        queue http parent root_data bandwidth 10M max 400M
        queue other parent root_data bandwidth 50M max 500M default
      None    : ''

`pf_queues_host`

    Description: Define the 'pf_queues_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # vio0
        queue root_data on vio0 bandwidth 1G
        queue ssh parent root_data bandwidth 5M min 1M max 100M
        queue http parent root_data bandwidth 10M max 400M
        queue other parent root_data bandwidth 50M max 500M default
      None    : ''

`pf_tables_default`

    Description: Define the 'pf_tables_default' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : |
      # private address space (RFC 1918)
      table <rfc1918> const { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 }
      # unique local addresses (RFC 4193)
      table <rfc4193> const { fc00::/7 }
    Options    :
      Examples: |
        # private address space (RFC 1918)
        table <rfc1918> const { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 }
        # unique local addresses (RFC 4193)
        table <rfc4193> const { fc00::/7 }
      None    : ''

`pf_tables_all`

    Description: Define the 'pf_tables_all' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # private address space (RFC 1918)
        table <rfc1918> const { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 }
        # unique local addresses (RFC 4193)
        table <rfc4193> const { fc00::/7 }
      None    : ''

`pf_tables_group`

    Description: Define the 'pf_tables_group' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # private address space (RFC 1918)
        table <rfc1918> const { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 }
        # unique local addresses (RFC 4193)
        table <rfc4193> const { fc00::/7 }
      None    : ''

`pf_tables_host`

    Description: Define the 'pf_tables_host' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        # private address space (RFC 1918)
        table <rfc1918> const { 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 }
        # unique local addresses (RFC 4193)
        table <rfc4193> const { fc00::/7 }
      None    : ''

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

    Version: 7.4
    Version: 7.5

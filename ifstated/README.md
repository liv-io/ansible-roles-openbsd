# ifstated

## Description

Interface State daemon

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: ifstated
  vars:
    ifstated_state: 'install'
```

### Enable

```
- hosts: all
  roles:
    - role: ifstated
  vars:
    ifstated_config:
      init-state auto
      carp_master = "carp410.link.up"
      state auto {
        if $carp_master
            set-state master
        if ! $carp_master
            set-state backup
      }
      state master {
          init {
              run "ifconfig wg0 up"
              run "logger -st ifstated 'state master'"
          }
          if ! $carp_master
              set-state backup
      }
      state backup {
          init {
              run "ifconfig wg0 down"
              run "logger -st ifstated 'state backup'"
          }
          if $carp_master
              set-state master
      }
```

### Disable

```
- hosts: all
  roles:
    - role: ifstated
  vars:
    ifstated_config:
      init-state auto
      carp_master = "carp410.link.up"
      state auto {
        if $carp_master
            set-state master
        if ! $carp_master
            set-state backup
      }
      state master {
          init {
              run "ifconfig wg0 up"
              run "logger -st ifstated 'state master'"
          }
          if ! $carp_master
              set-state backup
      }
      state backup {
          init {
              run "ifconfig wg0 down"
              run "logger -st ifstated 'state backup'"
          }
          if $carp_master
              set-state master
      }
```

### Remove

```
- hosts: all
  roles:
    - role: ifstated
  vars:
    ifstated_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: ifstated
  vars:
    ifstated_state: 'inactive'
```

## Parameters

### Role

`ifstated_state`

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

`ifstated_config`

    Description: Define the 'ifstated_config' option.
    Required   : False
    Value      : Arbitrary
    Type       : String
    Default    : ''
    Options    :
      Examples: |
        init-state auto
        carp_master = "carp410.link.up"
        state auto {
          if $carp_master
              set-state master
          if ! $carp_master
              set-state backup
        }
        state master {
            init {
                run "ifconfig wg0 up"
                run "logger -st ifstated 'state master'"
            }
            if ! $carp_master
                set-state backup
        }
        state backup {
            init {
                run "ifconfig wg0 down"
                run "logger -st ifstated 'state backup'"
            }
            if $carp_master
                set-state master
        }
      None    : ''

`ifstated_monit_state`

    Description: Control the 'ifstated_monit_state' option.
    Required   : False
    Value      : Predetermined
    Type       : Boolean
    Default    : False
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

    Version: 7.8
    Version: 7.9

# siege

## Description

Siege is an HTTP regression testing and benchmarking utility. It was designed
to let web developers measure the performance of their code under duress, to see
how it will stand up to load on the internet. Siege supports basic
authentication, cookies, HTTP and HTTPS protocols. It allows the user hit a web
server with a configurable number of concurrent simulated users. Those users
place the web-server "under siege."

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: siege
  vars:
    siege_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: siege
  vars:
    siege_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: siege
  vars:
    siege_state: 'inactive'
```

## Parameters

### Role

`siege_state`

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

## Conflicts

## Dependencies

### Packages

`siege`

    Version: >= 2.70
    Name   :
      OpenBSD 7.1: 'siege'
      OpenBSD 7.2: 'siege'

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

    Version: 7.1
    Version: 7.2

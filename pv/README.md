# pv

## Description

PV ("Pipe Viewer") is a tool for monitoring the progress of data through a
pipeline. It can be inserted into any normal pipeline between two processes to
give a visual indication of how quickly data is passing through, how long it has
taken, how near to completion it is, and an estimate of how long it will be
until completion.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: pv
  vars:
    pv_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: pv
  vars:
    pv_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: pv
  vars:
    pv_state: 'inactive'
```

## Parameters

### Role

`pv_state`

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

`pv`

    Version: >= 1.1
    Name   :
      OpenBSD 7.1: 'pv'
      OpenBSD 7.2: 'pv'

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
      Status: Stable
    Version: 7.2
      Status: Stable

# jq

## Description

Lightweight and flexible command-line JSON processor.

jq is like sed for JSON data - you can use it to slice and filter and map and
transform structured data with the same ease that sed, awk, grep and friends let
you play with text.

It is written in portable C, and it has zero runtime dependencies.

jq can mangle the data format that you have into the one that you want with very
little effort, and the program to do so is often shorter and simpler than you'd
expect.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: jq
  vars:
    jq_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: jq
  vars:
    jq_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: jq
  vars:
    jq_state: 'inactive'
```

## Parameters

### Role

`jq_state`

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

`jq`

    Version: >= 1.5
    Name   :
      OpenBSD 7.1: 'jq'
      OpenBSD 7.2: 'jq'

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

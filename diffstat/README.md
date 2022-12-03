# diffstat

## Description

The diff command compares files line by line. Diffstat reads the output of the
diff command and displays a histogram of the insertions, deletions and
modifications in each file. Diffstat is commonly used to provide a summary of
the changes in large, complex patch files.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: diffstat
  vars:
    diffstat_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: diffstat
  vars:
    diffstat_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: diffstat
  vars:
    diffstat_state: 'inactive'
```

## Parameters

### Role

`diffstat_state`

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

`diffstat`

    Version: >= 1.5
    Name   :
      OpenBSD 7.1: 'diffstat'
      OpenBSD 7.2: 'diffstat'

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

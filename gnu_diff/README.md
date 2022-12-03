# gnu_diff

## Description

GNU versions of diff utilities. You can use the diff command to show differences
between two files, or each corresponding file in two directories. diff outputs
differences between files line by line in any of several formats, selectable by
command line options. This set of differences is often called a 'diff' or
'patch'. For files that are identical, diff normally produces no output; for
binary (non-text) files, diff normally reports only that they are different.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: gnu_diff
  vars:
    gnu_diff_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: gnu_diff
  vars:
    gnu_diff_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: gnu_diff
  vars:
    gnu_diff_state: 'inactive'
```

## Parameters

### Role

`gnu_diff_state`

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

`gnu-diff`

    Version: >= 3.3
    Name   :
      OpenBSD 7.1: 'gdiff'
      OpenBSD 7.2: 'gdiff'

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

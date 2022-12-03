# python_yaml

## Description

YAML is a data serialization format designed for human readability and
interaction with scripting languages. PyYAML is a YAML parser and emitter for
Python.
PyYAML features a complete YAML 1.1 parser, Unicode support, pickle support,
capable extension API, and sensible error messages. PyYAML supports standard YAML
tags and provides Python-specific tags that allow to represent an arbitrary
Python object.
PyYAML is applicable for a broad range of tasks from complex configuration files
to object serialization and persistance.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: python_yaml
  vars:
    python_yaml_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: python_yaml
  vars:
    python_yaml_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: python_yaml
  vars:
    python_yaml_state: 'inactive'
```

## Parameters

### Role

`python_yaml_state`

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

`python-yaml`

    Version: >= 3.10
    Name   :
      OpenBSD 7.1: 'py-yaml'
      OpenBSD 7.2: 'py-yaml'

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

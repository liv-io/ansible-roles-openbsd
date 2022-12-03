# python_jinja2

## Description

Jinja2 is a template engine written in pure Python. It provides a Django
inspired non-XML syntax but supports inline expressions and an optional
sandboxed environment.
If you have any exposure to other text-based template languages, such as Smarty
or Django, you should feel right at home with Jinja2. It's both designer and
developer friendly by sticking to Python's principles and adding functionality
useful for templating environments.

For more information on the usage and available configuration options,
consult the following sections.

## Usage

### Install

```
- hosts: all
  roles:
    - role: python_jinja2
  vars:
    python_jinja2_state: 'install'
```

### Remove

```
- hosts: all
  roles:
    - role: python_jinja2
  vars:
    python_jinja2_state: 'remove'
```

### Inactive

```
- hosts: all
  roles:
    - role: python_jinja2
  vars:
    python_jinja2_state: 'inactive'
```

## Parameters

### Role

`python_jinja2_state`

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

`python-jinja2`

    Version: >= 2.2
    Name   :
      OpenBSD 7.1: 'py-jinja2'
      OpenBSD 7.2: 'py-jinja2'

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

# CHANGES

This file lists changes made to the Ansible role. It follows semantic versioning
guidelines. The content is sorted in reverse chronological order and formatted
to allow easy grepping by scripts.

The headers are:
- bugs
- changes
- enhancements
- features

## 3.1.0 (2024-04-06)

### Changes

- Add support for OpenBSD 7.5
- Drop support for OpenBSD 7.3

## 3.0.2 (2024-03-15)

### Bugs

- Validate `pf` configuration files also in `disable` state

## 3.0.1 (2024-03-10)

### Bugs

- Do not use `quick` in `pf_filters_default` ruleset (last rule to match is the winner)

## 3.0.0 (2024-03-10)

### Changes

- Entirely redesign Ansible role
- Change `pf_filters` data structure from list of dictionaries to string
- Change `pf_macros` data structure from list of dictionaries to dictionary
- Change `pf_tables` data structure from list of dictionaries to string
- Move configuration files from `/etc/pf` to `/etc/pf.d`
- Add support for filter rules from other Ansible roles via `/etc/pf.d/includes.conf`

## 2.0.0 (2023-12-28)

### Changes

- Rename Ansible role from `openbsd_pf` to `pf`

## 1.1.0 (2023-10-19)

### Changes

- Add support for OpenBSD 7.4
- Drop support for OpenBSD 7.2

## 1.0.1 (2023-10-16)

### Enhancements

- Minor Ansible style improvements

## 1.0.0 (2023-08-08)

### Changes

- Turn string state parameters into boolean

## 0.2.0 (2023-04-10)

### Changes

- Add support for OpenBSD 7.3
- Drop support for OpenBSD 7.1

## 0.1.0 (2022-10-22)

### Features

- Initial release

# CHANGES

This file lists changes made to the Ansible role. It follows semantic versioning
guidelines. The content is sorted in reverse chronological order and formatted
to allow easy grepping by scripts.

The headers are:
- bugs
- changes
- enhancements
- features

## 2.3.0 (2024-10-11)

### Changes

- Add support for OpenBSD 7.6
- Drop support for OpenBSD 7.4

## 2.2.0 (2024-04-06)

### Changes

- Add support for OpenBSD 7.5
- Drop support for OpenBSD 7.3

## 2.1.2 (2024-01-15)

### Bugs

- Remove all `authorized_keys` if `authorized_keys` parameter is empty or undefined

## 2.1.1 (2023-12-25)

### Bugs

- Support empty `authorized_keys` parameter

## 2.1.0 (2023-10-19)

### Changes

- Add support for OpenBSD 7.4
- Drop support for OpenBSD 7.2

## 2.0.1 (2023-10-16)

### Enhancements

- Minor Ansible style improvements

## 2.0.0 (2023-08-08)

### Changes

- Turn string state parameters into boolean

## 1.0.0 (2023-07-14)

### Changes

- Redesign `authorized_keys` management

### Enhancements

- Add task to manage primary group
- Remove dependency on Ansible role `group`

## 0.2.0 (2023-04-10)

### Changes

- Add support for OpenBSD 7.3
- Drop support for OpenBSD 7.1

## 0.1.0 (2022-10-22)

### Features

- Initial release

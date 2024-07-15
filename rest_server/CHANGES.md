# CHANGES

This file lists changes made to the Ansible role. It follows semantic versioning
guidelines. The content is sorted in reverse chronological order and formatted
to allow easy grepping by scripts.

The headers are:
- bugs
- changes
- enhancements
- features

## 2.0.0 (2024-07-15)

### Changes

- Remove option `--no-auth`

### Features

- Add option `--append-only`
- Add option `--htpasswd-file /etc/rest-server/htpasswd`
- Add option `--private-repos`

### Enhancements

- Update rest-server to version 0.12.1

## 1.3.0 (2024-04-06)

### Changes

- Add support for OpenBSD 7.5
- Drop support for OpenBSD 7.3

## 1.2.0 (2024-03-12)

### Bugs

- Fix `monit` check task

### Features

- Add parameter `rest_server_pf_filters`
- Add parameter `rest_server_pf_state`

## 1.1.0 (2023-10-19)

### Changes

- Add support for OpenBSD 7.4
- Drop support for OpenBSD 7.2

## 1.0.2 (2023-10-16)

### Enhancements

- Minor Ansible style improvements

## 1.0.1 (2023-08-16)

### Bugs

- Update monit tasks according to different states

## 1.0.0 (2023-08-08)

### Changes

- Turn string state parameters into boolean

## 0.3.1 (2023-06-26)

### Enhancements

- Remove role dependency and add package task instead

## 0.3.0 (2023-04-24)

### Features

- Update rest-server to version 0.12.0

## 0.2.0 (2023-04-10)

### Changes

- Add support for OpenBSD 7.3
- Drop support for OpenBSD 7.1

## 0.1.0 (2022-10-22)

### Features

- Initial release

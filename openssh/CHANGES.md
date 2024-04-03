# CHANGES

This file lists changes made to the Ansible role. It follows semantic versioning
guidelines. The content is sorted in reverse chronological order and formatted
to allow easy grepping by scripts.

The headers are:
- bugs
- changes
- enhancements
- features

## 1.2.1 (2024-04-03)

### Changes

- Remove unused and deprecated parameter `openssh_rsa_authentication`

### Features

- Add parameter `openssh_login_grace_time`
- Add parameter `openssh_max_auth_tries`
- Add parameter `openssh_max_startups`

## 1.2.1 (2024-03-12)

### Bugs

- Fix `monit` and `pf` check task

## 1.2.0 (2024-03-11)

### Bugs

- Fix `monit` check task

### Features

- Add parameter `openssh_pf_filters`
- Add parameter `openssh_pf_state`

## 1.1.1 (2024-03-08)

### Enhancements

- Reduce monit protocol timeout from 60 to 10 seconds

## 1.1.0 (2023-10-19)

### Changes

- Add support for OpenBSD 7.4
- Drop support for OpenBSD 7.2

## 1.0.3 (2023-10-16)

### Enhancements

- Minor Ansible style improvements

## 1.0.2 (2023-08-17)

### Enhancements

- Increase monit protocol check timeout

## 1.0.1 (2023-08-16)

### Bugs

- Update monit tasks according to different states

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

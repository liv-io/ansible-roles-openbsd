# CHANGES

This file lists changes made to the Ansible role. It follows semantic versioning
guidelines. The content is sorted in reverse chronological order and formatted
to allow easy grepping by scripts.

The headers are:
- bugs
- changes
- enhancements
- features

## 1.8.0 (2025-10-22)

### Changes

- Add support for OpenBSD 7.8
- Drop support for OpenBSD 7.6

## 1.7.0 (2025-05-10)

### Changes

- Add support for OpenBSD 7.7
- Drop support for OpenBSD 7.5

## 1.6.0 (2024-10-11)

### Changes

- Add support for OpenBSD 7.6
- Drop support for OpenBSD 7.4

## 1.5.0 (2024-04-28)

### Features

- Add support for `preshared_key`

## 1.4.0 (2024-04-06)

### Changes

- Add support for OpenBSD 7.5
- Drop support for OpenBSD 7.3

## 1.3.0 (2024-03-12)

### Bugs

- Fix `monit` check task

### Features

- Add parameter `wireguard_pf_filters`
- Add parameter `wireguard_pf_state`

## 1.2.0 (2024-02-14)

### Features

- Add option to define routes

## 1.1.0 (2023-10-19)

### Changes

- Add support for OpenBSD 7.4
- Drop support for OpenBSD 7.2

## 1.0.3 (2023-10-16)

### Enhancements

- Minor Ansible style improvements

## 1.0.2 (2023-08-21)

### Bugs

- Only reload WireGuard network interfaces

## 1.0.1 (2023-08-08)

### Bugs

- Fix parentheses in `hostname.config` template
- Fix `wireguard_monitor_monit_state` in `config.yml`

## 1.0.0 (2023-08-08)

### Changes

- Turn string state parameters into boolean

## 0.2.0 (2023-07-19)

### Features

- Add parameter `wireguard_monitor_monit_state`

## 0.1.1 (2023-07-18)

### Bugs

- Add missing command statement in `hostname_if` template

## 0.1.0 (2023-07-18)

### Features

- Initial release

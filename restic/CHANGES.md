# CHANGES

This file lists changes made to the Ansible role. It follows semantic versioning
guidelines. The content is sorted in reverse chronological order and formatted
to allow easy grepping by scripts.

The headers are:
- bugs
- changes
- enhancements
- features

## 1.0.2 (2023-10-16)

### Enhancements

- Minor Ansible style improvements

## 1.0.1 (2023-08-16)

### Enhancements

- Minor script improvement

## 1.0.0 (2023-08-08)

### Changes

- Turn string state parameters into boolean

## 0.3.0 (2023-08-04)

### Changes

- Remove default value for parameter `restic_password`
- Remove default value for parameter `restic_server_address`
- Remove default value for parameter `restic_server_password`
- Remove default value for parameter `restic_server_username`

### Enhancements

- Overhaul script

### Features

- Add parameter `restic_http_proxy`
- Add parameter `restic_https_proxy`
- Add parameter `restic_repository_name`

## 0.2.2 (2023-05-03)

### Enhancements

- Remove if-statement for `restic_run_backup_exit` Prometheus metric

## 0.2.1 (2023-05-01)

### Enhancements

- Overhaul script

## 0.2.0 (2023-04-10)

### Changes

- Add support for OpenBSD 7.3
- Drop support for OpenBSD 7.1

## 0.1.0 (2022-10-22)

### Features

- Initial release

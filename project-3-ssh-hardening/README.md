# Project 03 – SSH Hardening

## Objective

Harden SSH access on an Ubuntu Linux server by applying basic security controls and validating the effective SSH configuration.

## Environment

- Operating System: Ubuntu 26.04 LTS
- Hostname: ubuntu-server-01
- User: kojo
- SSH Service: OpenSSH
- SSH Port: 22

## Security Controls Implemented

- Disabled direct root login
- Reduced maximum SSH authentication attempts from 6 to 3
- Confirmed public-key authentication is enabled
- Confirmed empty passwords are prohibited
- Verified SSH configuration syntax
- Verified effective SSH configuration
- Verified secure permissions on the `.ssh` directory
- Verified permissions on `authorized_keys`

## Configuration

The following SSH settings were applied:

    PermitRootLogin no
    MaxAuthTries 3

Password authentication was intentionally left enabled because public-key authentication had not yet been configured for the `kojo` account.

## Validation

SSH configuration was validated using:

    sudo sshd -t

Effective settings were verified using:

    sudo sshd -T

The final configuration showed:

    permitrootlogin no
    maxauthtries 3
    permitemptypasswords no
    pubkeyauthentication yes
    passwordauthentication yes

## Screenshots

Screenshots documenting the project are included in the `screenshots` directory.

## Key Learning Outcome

This project demonstrates basic SSH security hardening, configuration validation, access control considerations, and the importance of verifying changes before restarting a critical remote-access service.

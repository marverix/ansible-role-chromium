# Ansible Role: Chromium

[![Build Status](https://travis-ci.com/marverix/ansible-role-chromium.svg?branch=master)](https://travis-ci.com/marverix/ansible-role-chromium)
![Ansible Quality Score](https://img.shields.io/ansible/quality/48217)
![Ansible Role](https://img.shields.io/ansible/role/48217)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)

Ansible role that installs Chromium on Linux.

## Features

- ✔️ Installing Chromium
- ✔️ Keeps Chromium up-to-date
- ✔️ Set up flags
- ✔️ Tested with Molecule Verify

## Supported Platforms

- ✔️ Ubuntu 16.04 (Xenial)
- ✔️ Ubuntu 18.04 (Bionic)
- ✔️ CentOS 7

## Requirements

None

## Role Variables

Variable | Description | Default Value
--- | --- | ---
`chromium_allow_root` | Should root be allowed to run Chromium? Sets `no-sandbox` flag. | `true`
`chromium_disable_gpu` | Should disable GPU? Sets `disable-gpu` flag. | `true`
`chromium_disable_web_security` | Should disable web security? Dangerous, but may be useful in some special dev cases. Sets `disable-web-security` flag. | `false`
`chromium_ignore_certificate_errors` | Should ignore certificate errors? Sets `ignore-certificate-errors` flag. | `false`
`chromium_custom_flags` | List of other flags to set. Flags **mustn't** be with `--` prefix! | `[]`

## Dependencies

None

## Example Playbook

1. The simplest one

    ```yml
    ---
    - hosts: all
      roles:
        - marverix.chromium

    ```

1. Install and allow root to run Chromium

    ```yml
    ---
    - hosts: all
      roles:
        - role: marverix.chromium
          vars:
            chromium_allow_root: true
    ```

1. Install, disable-web-security and set other custom flags

    ```yml
    ---
    - hosts: all
      roles:
        - role: marverix.chromium
          vars:
            chromium_disable_web_security: true
            chromium_custom_flags:
              - enable-experimental-accessibility-features
              - incognito
    ```

    BTW: Here is some good list of flags https://peter.sh/experiments/chromium-command-line-switches/

## License

ISC

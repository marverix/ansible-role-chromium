# Ansible Role: Chromium

[![Build Status](https://travis-ci.com/marverix/ansible-role-chromium.svg?branch=master)](https://travis-ci.com/marverix/ansible-role-chromium)
![Ansible Quality Score](https://img.shields.io/ansible/quality/48217)
![Ansible Role](https://img.shields.io/ansible/role/48217)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)

Ansible role that installs Ungoogled Chromium on Linux.

## Features

- ✔️ Installing [Ungoogled Chromium](https://github.com/macchrome/linchrome)
- ✔️ You can defined which version to install (by changing the URL)
- ✔️ Set up flags
- ✔️ Tested with Molecule Verify

## Supported Platforms

- ✔️ Ubuntu 18.04 (Bionic)
- ✔️ Ubuntu 20.04 (Focal)
- ✔️ CentOS 7
- ✔️ CentOS 8

## Requirements

None

## Role Variables

Variable | Description | Default Value
--- | --- | ---
`chromium_archive_url` | URL of Ungoogled Chromium archive | [link to Chromium 89](https://github.com/macchrome/linchrome/releases/download/v89.0.4389.114-r843830-portable-ungoogled-Lin64/ungoogled-chromium_89.0.4389.114_1.vaapi_linux.tar.xz)
`chromium_archive_sha1` | SHA1 of the archive | _SHA1 for the above package_
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

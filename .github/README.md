# ans-role-update-repo-servers

Ansible role to update list of linux distro's repo servers.

[![Release](https://img.shields.io/github/release/digimokan/ans-role-update-repo-servers.svg?label=release)](https://github.com/digimokan/ans-role-update-repo-servers/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Load Role Via `ansible-galaxy` Command](#load-role-via-ansible-galaxy-command)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Update list of repo servers, using an age criteria.
* Make a backup copy of the original list.

## Supported Operating Systems

* Arch Linux (updates `mirrorlist` file)

## Quick Start

### Load Role Via `ansible-galaxy` Command

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans-role-update-repo-servers
     version: master
     name: mirrors-update
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Update Arch Linux mirrorlist file"
         include_role:
           name: mirrors-update
   ```

## Role Options

See the role `defaults` file for full listing:

  * [defaults/main.yml](../defaults/main.yml)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans-role-update-repo-servers/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).


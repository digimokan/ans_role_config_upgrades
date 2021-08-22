# ans_role_config_upgrades

Ansible role to configure system and package upgrades.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_upgrades.svg?label=release)](https://github.com/digimokan/ans_role_config_upgrades/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Configure system upgrades.
* Configure package upgrades.
* Configure OS package repositories, and related updates.
* Install system and package management [utility scripts](../templates/).

## Supported Operating Systems

* Arch Linux
* FreeBSD

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_upgrades
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the main role, to configure system and package upgrades:

   ```yaml
   - name: "Configure system and package upgrades"
     ansible.builtin.include_role:
       name: ans_role_config_upgrades
   ```

4. Use role "utility task" (from the `inc` directory) to update OS package
   repositories:

   ```yaml
   - name: "Update OS package repositories"
     ansible.builtin.include_role:
       name: ans_role_config_upgrades
       tasks_from: inc/update_pkg_repo_list.yml
     vars:
       pkg_repo_list_age_cutoff: "1d"
   ```

### Use From Parent Role As Dependency

1. List in parent role's `meta/main.yml`, with `never` tag to avoid duplication:

   ```yaml
   dependencies:
     - src: https://github.com/digimokan/ans_role_config_upgrades
       tags:
         - never
   ```

2. Call role with step 3 or 4 from [Use From Playbook](#use-from-playbook)
   section.

## Role Options

See the role `defaults` file for main role vars listing:

  * [defaults](../defaults/main/)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_upgrades/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).


# Ansible Role: Drush

Installs Drush, a command line shell and scripting interface for Drupal

## Requirements

Tested on RedHat & CentOS 7

## Parent playbook

This role is a part of the playbook: [Aegir on CentOS 7](https://github.com/tovletoglou/ansible-playbook-aegir-centos).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):


The location of the entire drush installation (includes all the supporting files, as well as the `drush` executable file.

    drush_install_path: /usr/local/share/drush

The path where drush will be installed and available to your system. Should be in your user's `$PATH` so you can run commands simply with `drush` instead of the full path.

    drush_path: /usr/local/bin/drush

The version of Drush to install (examples: `"master"` for the bleeding edge, `"7.x"`, `"6.x"`, `"6.2.0"`). This should be a string as it refers to a git branch, tag, or commit hash.

    drush_version: "8.x"

Whether to keep Drush up-to-date with the latest revision of the branch specified by `drush_version`, and whether to force the update (e.g. overwrite local modifications to the drush repository).

    drush_keep_updated: yes
    drush_force_update: no

These options are the safest for avoiding GitHub API rate limits when installing Drush, and can be very helpful when working on dependencies/installation, but builds can be sped up substantially by changing the first option to --prefer-dist.

    drush_composer_cli_options: "--prefer-source --no-interaction"

## Dependencies

You should have `composer` on the system.

## Example Playbook

Call the role with the default variables

    - hosts: servers
      roles:
        - ansible-role-drush

Call the role and override the default variables

    - hosts: servers
      roles:
        - ansible-role-drush
      vars:
        drush_version: "8.x"
        drush_keep_updated: yes
        drush_force_update: yes

After the playbook runs, the `drush` command will be accessible from normal system accounts.

## License

MIT

newrelic
========

This role installs and configures [NewRelic](https://newrelic.com/) sysmond and agents (currently only php).

Requirements
------------

You need a [PHP installation](https://github.com/dpujadas/ansible-role-php) when using php agent.

Role Variables
--------------

- `newrelic_user`: User NewRelic will run as (default: 'newrelic')
- `newrelic_group`:  Group NewRelic will run as (default: newrelic_user)
- `newrelic_license_key`: NewRelic license key (Ex: 'aowlrefn9cwoe8h')
- `newrelic_init_system`: OS init system (upstart|systemd|runit). Docker phusion/baseimage uses 'runit'. (default 'upstart')
- `newrelic_skip_notify`: Skip notify handler (useful when testing without license key) (default: 'false')
- `newrelic_sysmond`:  Install NewRelic sysmond or not (default: False)
- `newrelic_sysmond_loglevel`: Level of detail you want in the log file (default: 'info')
- `newrelic_sysmond_hostname`: If defined, sets the name of the host (Ex: 'docker-travis')
- `newrelic_apm`: NewRelic agent to install (Ex: 'php'). When set, role installs newrelic-daemon, too. (default: '')
- `newrelic_apm_options`: List of directives for daemon config file (default: empty list)
- `newrelic_php_options`: List of directives for php agent config file (default: empty list)
- `newrelic_php_mods_dir`: Path to php modules config dir (Ex: '/etc/php/5.6/mods-available')

Example Playbook
----------------

    - hosts: servers
      roles:
        - {
          role: newrelic,
          newrelic_sysmond: True,
          newrelic_apm: 'php',
          newrelic_php_mods_dir: '/etc/php/5.6/mods-available'
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-newrelic.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-newrelic)

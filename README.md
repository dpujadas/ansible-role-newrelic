newrelic
========

This role installs and configures [NewRelic](https://newrelic.com/) daemon and, optionally, sysmond and agents (currently only php).

Role Variables
--------------

- `newrelic_user`: User NewRelic will run as (default: 'newrelic')
- `newrelic_group`:  Group NewRelic will run as (default: newrelic_user)
- `newrelic_license_key`: NewRelic license key (Ex: 'aowlrefn9cwoe8h')
- `newrelic_init_system`: OS init system. Docker phusion/baseimage uses 'runit'. (default 'upstart')
- `newrelic_skip_notify`: Skip notify handler (useful when testing without license key) (default: 'false')
- `newrelic_sysmond`:  Install NewRelic sysmond or not (default: False)
- `newrelic_sysmond_loglevel`: Level of detail you want in the log file (default: 'info')
- `newrelic_sysmond_hostname`: Sets the name of the host (Ex: 'docker-travis')

Example Playbook
----------------

    - hosts: servers
      roles:
        - {
          role: newrelic,
          newrelic_sysmond: True
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-newrelic.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-newrelic)

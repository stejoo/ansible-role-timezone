Ansible role timezone
=========

Ansible role that adjusts the timezone setting of a machine for you.

I found others that do this, but may use an old style, custom method or call
 `timedatectl` as a command, instead of using the Ansible *timezone* module. So
that's what this role uses.

Requirements
------------

This role depends on collection [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/).


Role Variables
--------------

A description of the settable variables for this role:

| Variable                               | Default                                  | Description                                                    |
|----------------------------------------|------------------------------------------|----------------------------------------------------------------|
| `timezone_zonename`                    | Etc/UTC                                  | Name of the timezone for the system clock.                     |
| `timezone_hwclock`                     | *null*                                   | Set the hardware clock in UTC or in local time. (*Linux only*) |
| `timezone_restart_cron_daemon_allowed` | yes                                      | Allow restart of cron daemon after timezone has changed.       |
| `timezone_cron_daemon`                 | `crond` on RedHat's<br>`cron` on others  | Service name of the cron daemon to call to restart.            |

Variable `timezone_cron_daemon` is distribution specific and read from `vars/`
 when the role is run. In case your distribution or OS is not represented
correctly or missing, please add it by creating a pull request.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: stejoo.timezone, timezone_zonename: Europe/Amsterdam }

License
-------

GPLv3

Author Information
------------------

Stefan Joosten

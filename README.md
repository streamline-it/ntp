Role Name
=========

ntp

This will install/configure the ntp service on a FreeBSD or RedHat host.  Re RedHat only on version 6-7.

Requirements
------------

FreeBSD and RHEL (versions 6, 7)

Role Variables
--------------

# Defaults

#list server(s) to pull time from and settings
# example:
# ntp_servers:
#   - server.example.com -iburst
#
ntp_servers:

# if this is true default pool entries are commented out
# if this is false default pool entries are left alone

ntp_enable_servers_over_pool: false

# used to comment lines out in the config if user chost
# to use a server instead of a pool

# Vars section

#RedHat versions

ntp_pool_entries:
  - pool 0.rhel.pool.ntp.org iburst
  - pool 2.rhel.pool.ntp.org iburst

ntp_config_filepath: /etc/ntp.conf


# service name
ntp_svc: ntpd

ntp_pkg: ntp

#FreeBSD versions

ntp_pool_entries:
  - pool 0.freebsd.pool.ntp.org iburst
  - pool 2.freebsd.pool.ntp.org iburst

ntp_config_filepath: /etc/ntp.conf


# service name
ntp_svc: ntpd

ntp_pkg: ntp

Dependencies
------------

None.

Example Playbook
----------------

Configure host example:

- name: test ntp role for the host
  hosts: node8.freebsd13.example.com
  become: true

  vars:

    ntp_jail_it: false

  roles:

    - name: ntp

Configure a jail example:

- name: test ntp role for the jail
  hosts: node8.freebsd13.example.com
  become: true

  vars:


    ntp_jail_it: true
    ntp_jail_name: jp2_samba
    ntp_jail_prepath: /jails/jp2_samba

  roles:

    - name: ntp

License
-------

BSD

Author Information
------------------

streamline-it

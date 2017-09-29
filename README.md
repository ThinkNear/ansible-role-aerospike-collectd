Deprecated
==========

This role is no longer supported. It is left public only as an example.

## Ansible Role: Aerospike Collectd

[![Apache 2.0](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://raw.githubusercontent.com/DigitalSlideArchive/ansible-role-vips/master/LICENSE)
[![Build Status](https://travis-ci.org/ThinkNear/ansible-role-aerospike-collectd.svg?branch=master)](https://travis-ci.org/ThinkNear/ansible-role-aerospike-collectd)

An Ansible role that installs, configures, and runs collectd with the [Aerospike plugin](https://github.com/aerospike/aerospike-collectd) on Amazon and CentOS Linux.

This role can also enable collectd to publish metrics to Librato.

Requirements
------------

The server must run Amazon or CentOS.

This requires Ansible v2.

Role Variables
--------------

Available variables with default values are listed below (see defaults/main.yml):

    aerospike_collectd_plugin_version: 1.0.1
    
Controls the version of the aerospike plugin installed.
Go [here](https://github.com/aerospike/aerospike-collectd/releases) for a complete list of releases.

    aerospike_collectd_conf_dir: /etc/collectd.d

Controls where collectd configurations are installed. A useful reference for installing custom configurations.

    aerospike_collectd_install_dir: /usr/local/src

Controls where the aerospike collectd plugin is installed.

    aerospike_collectd_use_librato: false

Controls whether collectd publishes metrics to Librato. Go [here](https://www.librato.com/docs/kb/collect/integrations/collectd/index.html) for more details on using collectd with Librato.

    aerospike_collectd_librato_user: EMAIL
    
If `aerospike_collectd_use_librato` is enabled, controls the username credential for Librato.

    aerospike_collectd_librato_password: TOKEN
    
If `aerospike_collectd_use_librato` is enabled, controls the token credential for Librato.

    aerospike_collectd_aggregate_cpu: true
    
Controls whether CPU statistics are aggregated as an average.
This is useful to reduce the number of metrics sent to Librato.

    aerospike_collectd_interval: 10
    
Controls the collection interval of collectd.

    aerospike_collectd_max_read_interval: 86400
    
Controls the interval between queries after each failed attempt to get data.

  aerospike_collectd_sourcename: "{{ inventory_hostname }}"

Controls the prefix of the collectd sourcename.
The full name will have the instance ID as a postfix when deployed to AWS EC2.
For example, `web1-i-1234567`.
Otherwise the name will have 'local' as a postfix.
For example, `web1-local`.

    aerospike_collectd_disks:
      - xvdb
      - xvdc

Controls the disks to monitor.


    aerospike_collectd_package_version

Controls the collectd package version installed.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      become: yes
      roles:
         - ThinkNear.aerospike-collectd

License
-------

ALv2

Author Information
------------------

This role was created in 2016 by Thinknear. 
http://thinknear.com

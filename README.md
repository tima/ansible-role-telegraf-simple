# Ansible Role: telegraf-simple

[![Build Status](https://travis-ci.org/tima/ansible-role-telegraf-simple.svg?branch=master)](https://travis-ci.org/tima/ansible-role-telegraf-simple)

A simplistic role for installing, configuring and running 
[Telegraf](https://github.com/influxdata/telegraf) on a Red Hat OS family host. 

This role is intentionally rudimentary and of limited functionality. It was developed 
to serve as an example of a basic role for those becoming familar with roles could
learn from.  

It does not use any role dependencies and only supports Red Hat OS family servers
that are managed using yum. It supports only a few configuration options. It does
not support plugins either. 

This role was derived from the Ansible lightbulb repository and was originally 
authored by James Martin jsmartin

## Requirements

None

## Role Variables

Available variables are listed below with default values (see `defaults/main.yml`):

    telegraf_influxdb_url: http://localhost:8086

This variable defines the InfluxDB system URL that Telegraf should feed its metrics.

    telegraf_influxdb_db_name: telegraf

This variable defines the name of the InfluxDB database the metrics should be stored.

## Dependencies

None

## Example Playbook

The most basic usage of this role in a play is as follows:

    - hosts: servers
      roles:
         - role: 'tima.telegraf-simple'

To setup a basic telegraf simple and direct its metrics to an external InfluxDB
system with a database name of "simple_stats" you could use any variable 
source to override the role's defaults values such as role params like this:

    - hosts: servers
      roles:
         - role: 'tima.telegraf-simple'
           telegraf_influxdb_url: 'http://influxdb.example.net:8086/'
           telegraf_influxdb_db_name: 'simple_stats'

Other means include play `vars`, inventory variables and `extra_vars` on the 
command line to name a few more. 

## Contributions and Feedback

Any contributions are welcome. For any bugs or feature requests,
please open an issue through Github.

## License

Apache

## Author

Originally created by [James S Martin](https://github.com/jsmartin) and was 
ported into this role by [Timothy Appnel](https://github.com/tima).


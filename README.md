# ssh

[![License](https://img.shields.io/badge/license-New%20BSD-blue.svg?style=flat)](https://raw.githubusercontent.com/ansiblebit/ssh_known_hosts/master/LICENSE)
[![Build Status](https://travis-ci.org/ansiblebit/ssh_known_hosts.svg?branch=master)](https://travis-ci.org/ansiblebit/ssh_known_hosts)

[![Platform](http://img.shields.io/badge/platform-debian-a80030.svg?style=flat)](#)
[![Platform](http://img.shields.io/badge/platform-ubuntu-dd4814.svg?style=flat)](#)

[![Project Stats](https://www.openhub.net/p/ansiblebit-ssh_known_hosts/widgets/project_thin_badge.gif)](https://www.openhub.net/p/ansiblebit-ssh_known_hosts/)

[Ansible][ansible] role to setup `/etc/ssh/known_hosts`.


## Tests

| Family | Distribution | Version | Test Status |
|:-:|:-:|:-:|:-:|
| Debian | Debian  | Jessie  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Debian  | Wheezy  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Yakkety | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Xenial  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Vivid   | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Trusty  | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#) |
| Debian | Ubuntu  | Precise | [![x86_64](http://img.shields.io/badge/x86_64-passed-006400.svg?style=flat)](#)  |


## Requirements

- ansible >= 2.0


## Role Variables

- **debug**: flag to run debug tasks.
- **ssh_config**: `ssh_config` file configuration.
- **ssh_config_path**: path to `ssh_config` file.
- **ssh_known_hosts_global_scan**: list of hostname that after a `keyscan` are added to the global `ssh_known_hosts` file.
- **ssh_known_hosts_global_path**: path to the `ssh_known_hosts` file.
- **ssh_known_hosts_user_scan**: list of hostnames that after a `keyscan` are added to the user's `known_hosts` file.


## Dependencies

None.


## Playbooks

    - hosts: servers
      vars:
        ssh_known_hosts_global_scan:
          - github.com
        ssh_known_hosts_user_scan:
          - user: vagrant
            hosts:
              - bitbucket.com

      roles:
         - role: ssh


## Tags

- **configuration**: configuration tasks.
- **debug**: task to debug role variables.
- **installation**: installation tasks.
- **validation**: task to validate role variables.


## Test

To run the tests you will need to install:

- [tox](https://tox.readthedocs.org/)
- [vagrant](https://www.vagrantup.com/)

To run all tests against all pre-defined OS/distributions * ansible versions:

```
$ tox
```

To run tests for `trusty64`:

```
$ cd tests
$ bash test_idempotence.sh --box trusty64.vagrant.dev
# log file will be stores under tests/log
```

To perform debugging on a specific environment:

```
$ cd tests
$ vagrant up trusty64.vagrant.dev

# to provision using the test.yml playbook (as many time as you need)
$ vagrant provision trusty64.vagrant.dev

# to access the Vagrant box
$ vagrant ssh trusty64.vagrant.dev
```


## Links

- [stackoverflow > http://stackoverflow.com/questions/12136998/how-to-check-if-a-host-is-in-your-known-host-ssh](http://stackoverflow.com/questions/12136998/how-to-check-if-a-host-is-in-your-known-host-ssh)
- [gist : bradland/ssh-known-hosts-mgmt.sh](https://gist.github.com/bradland/1315165)

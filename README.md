Ansible Role: Oracle Instant Client
=========

An Ansible Role that to install Oracle Instant Client

Before using this role, Oracle Instant Client installer files must be placed on files directory.
Make sure that those files have same version & patch.

And also make sure that `ldconfig` binary is already available in the system.

You can use `yum whatprovides ldconfig` to search all packages that providing ldconfig binary.
As on Centos/RHEL 7, ldconfig is provided by `glibc` package.
Then use `yum install glibc`, if it is still not installed in the system.

As a notice, the limitation of this role is that only RPM installer files that can be used.

Requirements
------------

This role needs no special requirements, except Oracle Instant Client installers and sudo access

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):


```yaml
---
oic_tmp_dir: /tmp
oic_clear_installers: yes
oic_version: "12.2"
oic_patch_version: "0.1.0-1"
oic_installers:
  - "oracle-instantclient{{ oic_version }}-basic-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
  - "oracle-instantclient{{ oic_version }}-devel-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
  - "oracle-instantclient{{ oic_version }}-jdbc-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
  - "oracle-instantclient{{ oic_version }}-odbc-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
  - "oracle-instantclient{{ oic_version }}-sqlplus-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
---
- name: Prepare CentOS 7 server
  hosts: centos7
  roles:
    - role: adipriyantobpn.oracle-instantclient
      oic_tmp_dir: /tmp
      oic_clear_installers: no
      oic_version: "12.2"
      oic_patch_version: "0.1.0-1"
      oic_installers:
        - "oracle-instantclient{{ oic_version }}-basic-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
        - "oracle-instantclient{{ oic_version }}-devel-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
        - "oracle-instantclient{{ oic_version }}-jdbc-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
        - "oracle-instantclient{{ oic_version }}-sqlplus-{{ oic_version }}.{{ oic_patch_version }}.x86_64.rpm"
```

License
-------

BSD

Author Information
------------------

This role was created in 2017 by [Adi Priyanto](https://github.com/adipriyantobpn) as a learning purpose for community.
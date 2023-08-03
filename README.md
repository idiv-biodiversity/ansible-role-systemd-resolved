Ansible Role: systemd-resolved
==============================

An Ansible role that configures **systemd-resolved**.

Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

Requirements
------------

- Ansible 2.9

Role Variables
--------------

Define your DNS servers:

```yml
systemd_resolved_servers:
  - a.b.c.1
  - a.b.c.2

systemd_resolved_fallback_servers:
  - d.e.f.1
  - d.e.f.2
```

Define your domains:

```yml
systemd_resolved_domains:
  - example.com
```

Other variables in the order they show up along with their default values:

```yml
systemd_resolved_dnssec: 'no'
systemd_resolved_dns_over_tls: 'no'
systemd_resolved_multicast_dns: 'yes'
systemd_resolved_llmnr: 'yes'
systemd_resolved_cache: yes
systemd_resolved_cache_from_localhost: no
systemd_resolved_dns_stub_listener: 'yes'
systemd_resolved_dns_stub_listener_extra: ''
systemd_resolved_read_etc_hosts: yes
systemd_resolved_resolve_unicast_single_label: no
```

For more information, read `man 5 resolved.conf`.

Dependencies
------------

- collection **ansible.posix**

Example Playbook
----------------

Add to `requirements.yml`:

```yml
---

- src: idiv-biodiversity.systemd_resolved

...
```

Download:

```console
$ ansible-galaxy install -r requirements.yml
```

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: head server
  hosts: head

  roles:
    - role: idiv-biodiversity.systemd_resolved
      tags:
        - systemd-resolved

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv-biodiversity.systemd_resolved
    tags:
      - systemd-resolved

...
```

License
-------

MIT

Author Information
------------------

This role was created in 2019 by [Christian Krause][author] aka [wookietreiber
at GitHub][wookietreiber], HPC cluster systems administrator at the [German
Centre for Integrative Biodiversity Research (iDiv)][idiv].

[author]: https://www.idiv.de/en/groups_and_people/employees/details/61.html
[idiv]: https://www.idiv.de/
[wookietreiber]: https://github.com/wookietreiber

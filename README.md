Ansible Role - ball6847.role.apt-cacher
============================================

Setup apt cacher via docker and docker-compose.

Requirements
------------

- docker
- docker-compose

Role Variables
--------------

**apt_cacher_path**: `/opt/apt-cacher`

Path to place docker-compose.yml file into.

**apt_cacher_volume**: `/var/cache/apt-cacher`

Path on host to store apt cacher data.

**apt_cacher_port**: `3142`

Port to run apt cacher on.

**apt_cacher_compose_file**: `templates/docker-compose.yml.j2`

Path to `docker-compose.yml` of apt-cacher, this role comes with basic `docker-compose.yml`, if you need to configure these values yourself,
make sure you override this variable and point it to your real `docker-compose.yml` file.

Please note that you should always prepend your value with `{{ playbook_dir }}` to make it completely ignore files in role.


Dependencies
------------

none

Example Playbook
----------------

```yml
- name: Setup Apt Cacher
  hosts: all
  become: yes
  tags: [ apt_cacher ]
  roles:
    - { role: ball6847.role.apt_cacher }
```

To override default template file.

```yml
- name: Setup Apt Cacher
  hosts: all
  become: yes
  tags: [ apt_cacher ]
  roles:
    - { role: ball6847.role.apt_cacher, apt_cacher_compose_file: "{{ playbook_dir }}/templates/docker-compose.yml.j2" }
```

License
-------

BSD

Author Information
------------------

Porawit Poboonma

Credits
------

- [clue/apt-cacher](https://hub.docker.com/r/clue/apt-cacher/) - Docker image used by this role.

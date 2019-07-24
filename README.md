[![Build Status](https://travis-ci.org/novomatic-tech/ansible-role-kafka-in-docker.svg?branch=master)](https://travis-ci.org/novomatic-tech/ansible-role-kafka-in-docker) [![License](https://img.shields.io/badge/license-Apache%202-green.svg)](https://github.com/novomatic-tech/ansible-role-kafka-in-docker/blob/master/LICENSE) [![Ansible Role Name](https://img.shields.io/ansible/role/42270.svg)](https://galaxy.ansible.com/novomatic-tech/kafka_in_docker) [![Ansible Role counter](https://img.shields.io/ansible/role/d/42270.svg)](https://galaxy.ansible.com/novomatic-tech/kafka_in_docker)
# ansible-role-kafka-in-docker
Role to install and configure Kafka cluster base on official and some community containers.
Role is used in our organization for different testing purposes and demo enviromnets.

ToDo
--------------
*   Add correct test to check if cluster is correctly setup
*   Switch docker container to use other `USER` than root
*   Configure friewalld and ufw rules to expose only kafka traffic ports outside hosts.
*   Enable kafka persistence


Role Variables
--------------

All default variables are predefined in [defaults/main.yml](defaults/main.yml).

Example Playbook
----------------

Example playbook usage.

```
- hosts: ubuntu18
  vars:
  host_domain: test.env.com
  configure_etc_hosts: false
  service_prefix: test-project
   # Below there are some ansible values that could be also define in ansible.cfg
   ansible_become: yes
  roles:
    - geerlingguy.docker
    - ansible-role-kafka-in-docker
```

License
-------
Apache 2.0

Author Information
------------------

This role was created in 2019 for Novomatic Technologies Poland purposes.


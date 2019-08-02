[![Build Status](https://travis-ci.org/novomatic-tech/ansible-role-kafka-in-docker.svg?branch=master)](https://travis-ci.org/novomatic-tech/ansible-role-kafka-in-docker) [![License](https://img.shields.io/badge/license-Apache%202-green.svg)](https://github.com/novomatic-tech/ansible-role-kafka-in-docker/blob/master/LICENSE) [![Ansible Role Name](https://img.shields.io/ansible/role/42270.svg)](https://galaxy.ansible.com/novomatic-tech/kafka_in_docker) [![Ansible Role counter](https://img.shields.io/ansible/role/d/42270.svg)](https://galaxy.ansible.com/novomatic-tech/kafka_in_docker)
# ansible-role-kafka-in-docker
A role to install and configure the Kafka cluster base on official containers and some community containers.
The role is used in our organization for different testing purposes and demo environments.

To Do
--------------
*   Add correct test to check if cluster is correctly set up.
*   Configure firewalld and ufw rules to expose only kafka traffic ports outside hosts.

Role Variables
--------------

All default variables are predefined in [defaults/main.yml](defaults/main.yml).
If you switch to `official zookeeper image`, the variable facts below need to be changed in [tasks/main.yml](defaults/main.yml):
*   `zoo_server` fact needs to be modified to:
    ```
    zoo_servers: "{{ zoo_servers + [' server.' + ( id | int + 1 ) | string + '=' + zoo_prefix + '-' + ( id | int + 1 ) | string  + ':' + zoo_ports.mgmt ] }}"
    ```
*   `ZOOKEEPER_SERVER_ID` to `ZOO_SERVER_ID`
*   `ZOOKEEPER_CLIENT_PORT` to `ZOO_PORT`
*   `ZOOKEEPER_SERVERS` to `ZOO_SERVERS`


Example Playbook
----------------

Example playbook usage:

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

This role was created in 2019 for the purposes of Novomatic Technologies Poland.


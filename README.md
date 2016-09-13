Jenkins Swarm Client
==========
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Variables](#variables)
- [Usage](#usage)

# Introduction
This is an ansible role to install and configure a jenkins-swarm-client onto a systemd based system.
This will automatically register (or deregister if the client is stopped) the host to your jenkins master as a node.

# Requirements
- Ansible >= 2.1
- Swarm plugin needs to be installed on jenkins master (see: https://wiki.jenkins-ci.org/display/JENKINS/Swarm+Plugin)
- Java needs to be installed

# Variables
| Name | Description | Default |
|:-----|:------------|:--------|
|swarm_client_installation_dir| installation folder for swarm-client | /construction/swarm-client
|swarm_client_local_user| installation user | root
|swarm_client_local_group| installation group | root
|swarm_client_version| client version | 2.2
|swarm_client_name | local jar file name | 'swarm-client-{{ swarm_client_version }}.jar'
|swarm_client_url| download url | 'https://repo.jenkins-ci.org/releases/org/jenkins-ci/plugins/swarm-client/{{ swarm_client_version }}/swarm-client-{{ swarm_client_version }}-jar-with-dependencies.jar'
|swarm_client_service_path| path to store systemd file | /etc/systemd/system/
|swarm_client_service_file| systemd unit file name | swarm_client.service
|swarm_client_service_state| service state | started
|swarm_client_service_enabled| service enabled | true
|swarm_client_service_template| systemd template file | swarm_client.service.j2
|swarm_client_working_dir| jenkins working dir |  /construction/jenkins-slave
|swarm_client_description| description shown in jenkins | "I am a swarm node"
|swarm_client_executors| number of executors on this node | 1
|swarm_client_labels| labels to use | useme
|swarm_client_jenkins_master| jenkins master url to connect to | http://localhost:8080/
|swarm_client_jenkins_master_user| username used for connection | changeme
|swarm_client_jenkins_master_pass| changeme password used for connection |
|swarm_client_mode| mode to start with | exclusive
|swarm_client_jenkins_name| displayed name in jenkins | swarm-node
|swarm_client_retries| retry count | 5

# Usage

Install swarm client package
```yaml
---
- hosts: servers
  roles:
  - role: swarm-client
```

# License

BSD

# Author Information

[Bjoern Jessen-Noak]

[Bjoern Jessen-Noak]: mailto:djsm@gmx.de

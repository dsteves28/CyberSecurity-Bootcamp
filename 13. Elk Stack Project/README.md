# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![FullNetworkWorkMap](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/13.%20Elk%20Stack%20Project/FullNetworkWorkMap.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the *playbook* file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- As websites receive more traffic, more servers can be added to the group (“pool”) of servers that the load balancer has access to.
This helps distribute traffic evenly across the servers and mitigates DoS attacks.
- The jump server acts as a single audit point for traffic and also a single place where user accounts can be managed. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat collects metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    | Container| 10.0.0.5   | Docker           |
| Web 2    | Container| 10.0.0.6   | Docker           |
| ELK Server| Server  | 10.1.0.4   | Hypervisor       |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 69.180.139.64

Machines within the network can only be accessed by Jump Box.
- Jump Box - Public IP (52.152.146.45) Private IP (10.0.0.4)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 69.180.139.64        |
| Web 1    | No                  | 10.0.0.5             |
| Web 2    | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Its easier to set up more than one server quickly and identically.

The playbook implements the following tasks:
- Enable use of more memory
- Install Docker
- Install Pip3
- Install Docker python module
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![dockerps](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/13.%20Elk%20Stack%20Project/dockerps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1 - Public IP (20.85.208.197) - Private IP (10.0.0.5) 
- Web 2 - Public IP (20.85.208.197) - Private IP (10.0.0.6)

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat for file changes and Metricbeat periodically collets metric data from the pc and server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible control node.
- Update the config file to include Web 1 and Web 2.
- Run the playbook, and navigate to ansible container to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook? Where do you copy it? .yml & Copy this onto the Elk server
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Ansible config.yml and the machine Filebeat is installed on is specified in the Ansible config.yml
- URL to navigate to in order to check that the ELK server is running. http:// (ELK Server Public IP) :5601/app/kibana#/home 
  - My server is http://40.83.184.101:5601/app/kibana#/home

![ron](https://imgur.com/4ao73O6.gif)

  ## ELK.yml
```
  ---
- name: Config elk VM with Docker
  hosts: elk
  remote_user: sysadmin
  become: true
  tasks:

  - name: Use more memory
    sysctl:
      name: vm.max_map_count
      value: '262144'
      state: present
      reload: yes

  - name: docker.io
    apt:
      force_apt_get: yes
      update_cache: yes
      name: docker.io
      state: present

  - name: Install pip3
    apt:
      force_apt_get: yes
      name: python3-pip
      state: present

  - name: Install Docker python module
    pip:
      name: docker
      state: present

  - name: download and launch a docker elk container
    docker_container:
      name: elk
      image: sebp/elk:761
      state: started
      restart_policy: always
      # List of ports that ELK runs on
      published_ports:
          -  5601:5601
          -  9200:9200
          -  5044:5044

  - name: Enable docker service
    systemd:
      name: docker
      enabled: yes
```
  ## Filebeat_config.yml

[Filebeat_config.yml](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/13.%20Elk%20Stack%20Project/Filebeat_config.yml)

  ## Filebeat.yml
```
  ---
- name: Installing and Launch Filebeat
  hosts: webservers
  become: yes
  tasks:
  - name: Download filebeat .deb file
    command: curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.0-amd64.deb

  - name: Install filebeat .deb
    command: dpkg -i filebeat-7.4.0-amd64.deb

    # Use copy module
  - name: Drop in filebeat.yml
    copy:
      src: /etc/ansible/files/filebeat-config.yml
      dest: /etc/filebeat/filebeat.yml

  - name: Enable and Configure System Module
    command: filebeat modules enable system

  - name: Setup filebeat
    command: filebeat setup

  - name: Start filebeat service
    command: service filebeat start

    # Use systemd module
  - name: Enable service filebeat on boot
    systemd:
      name: filebeat
      enabled: yes
  ```

## Metricbeat_config.yml

[Metricbeat_config.yml](https://github.com/dsteves28/CyberSecurity-Bootcamp/blob/main/13.%20Elk%20Stack%20Project/Metricbeat_config.yml)

## Metricbeat.yml
```
---
- name: Install metric beat
  hosts: webservers
  become: true
  tasks:
  - name: Download metricbeat
    command: curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.4.0-amd64.deb

  - name: install metricbeat
    command: dpkg -i metricbeat-7.4.0-amd64.deb

  - name: drop in metricbeat config
    copy:
      src: /etc/ansible/files/metricbeat-config.yml
      dest: /etc/metricbeat/metricbeat.yml

  - name: enable and configure docker module for metric beat
    command: metricbeat modules enable docker

  - name: setup metric beat
    command: metricbeat setup

  - name: start metric beat
    command: service metricbeat start

  - name: Enable service metricbeat on boot
    systemd:
      name: metricbeat
      enabled: yes
```
![bird](https://i.imgur.com/W1pogtE.gif)

# Project-1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[https://app.diagrams.net/#G1_eD4tGE832xX_KGuyHPgWXJ48WEVmiHA] ( Network topology of Project )

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/mhaque92/Project-1/blob/main/Ansible/Filebeat/Filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and available, in addition to restricting traffic to the network.
- Load balancers can defend an organization against denial-of-service (DDos) attacks. The advantage of having a jumpbox is being able to use a virtual machine that has hardended security and can manage other systems within your security sone or overal network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat monitors the log files or locations that you specify.
- Metricbeat records the metrics and statistics from the operation system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name    | Function    | IP Address | Operating System |
|---------|-------------|------------|------------------|
|         |             |            |                  |
| Jumpbox | Gateway     | 10.0.0.4   | Linux            |
| Web-1   | Webserver 1 | 10.0.0.7   | Linux            |
| Web-2   | Webserver 2 | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 66.108.39.253


Machines within the network can only be accessed by JumpBox virtual machine.
- The Jumpbox has access to the ELK VM. The IP address of the JumpBox is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name    | Publicly Accessible  | Allowed IP Address |
|---------|----------------------|--------------------|
|         |                      |                    |
| Jumpbox | No                   | 66.108.39.253      |
| Web-1   | No                   | 10.0.0.4           |
| Web-2   | No                   | 10.0.0.4           |
| ELK     | No                   | 10.0.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows IT administrators to automate their daily tasks and save a lot of time.


The playbook implements the following tasks:
- Install Docker
- Install python3-pip
- Install Docker python module 
- Set the vm.max_map_count to 262144
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/mhaque92/Project-1/blob/main/Docker%20ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1, 10.0.0.7
- Web-2, 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify, which we use to see what changes or messages the log files have received such as kill commands. Metricbeat records the metrics and statistics from the operation system and from services running on the server, which we could use to look at how much RAM or CPU usage was being used on the webservers at certain time.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to /etc/ansible.
- Update the hosts file to include the machine, its IP, and ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to http://[your_VM_IP]:5601/app/kibana to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

Commands to use the Playbook
- nano ansible.cfg
- add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts
- Ctrl + x to save and exit file
- in the folder that install-elk.yml is in, run: cp install-elk.yml /etc/ansible
- nano install-elk.yml /etc/ansible
- name: installing elk hosts: [your_machine]
- Ctrl + x to save and exit file
- ansible-playbook install-elk.yml




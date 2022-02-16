# ElkStack-Project
Week 13 Elk Stack Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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
Load balancers protects the system from DDoS attacks by shifting attack traffic. Load Balancing contributes to the Availability aspect of security in regards to the CIA Triad.The advantage of a jump box is to give access to the user from a single node that can be secured and monitored

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
Filebeat watches for any information in the file system which has been changed and when it has. Also for log files/locations and collects log events. 
Metricbeat takes the metrics and statistics that collects and ships them to the output you specify.It also records metric and statistical data from the operating system and from services running on the server.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.


| Name    | Function | IP Address                               | Operating System |
|---------|----------|------------------------------------------|------------------|
| JumpBox | Gateway  | Public:20.121.217.106  Private: 10.0.0.4 | Linux            |
| Web1    | Server   | 10.0.0.5                                 | Linux            |
| Web2    | Server   | 10.0.0.6                                 | Linux            |
| Web3    | Server   | 10.0.0.7                                 | Linux            |
| Elk-VM1 | Elk      | Public:52.160.40.187 Private: 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
My Public IP address

Machines within the network can only be accessed by ssh.
JumpBoxProvisioner 10.0.0.4(Private) 20.121.217.106 (Public)

A summary of the access policies in place can be found in the table below.

| Name    | Publicly Accessible | Allowed IP Addresses |
|---------|---------------------|----------------------|
| JumpBox | Yes/No              | My Public IP         |
| Web1    | No                  | 10.0.0.4             |
| Web2    | No                  | 10.0.0.4             |
| Web3    | No                  | 10.0.0.4             |
| Elk-VM1 | No                  | Private: 10.0.0.4    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
It allows you to deploy to multiple servers using a single playbook

The playbook implements the following tasks:
-Install docker.io
-Install Python-pip
-Install docker container
-Launch docker container: elk
-Command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web1: 10.0.0.5 
Web2: 10.0.0.6 
Web3: 10.0.0.7

We have installed the following Beats on these machines:
Filebeat & Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat collects metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the the configuration file to include the ElkVM1's private Ip addresses
- Run the playbook, and navigate to ElkVM1 to check that the installation worked as expected


- _Which file is the playbook? Where do you copy it?/etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? /etc/ansible/hosts file to add webserver/elkserver ip addresses
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana




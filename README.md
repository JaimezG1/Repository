# Repository
Project 1 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Repository/Diagrams/Project_1_Diagram.png 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
- Load balancers provide security by protecting the system from attacks such as DDos attacks. The advantage of having a jumpbox is reducing the risks and having the seperation of admins and others that aren't authorized access.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- Filebeat monitors log files.
- Metricbeat records metrics from the operating system.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   |Linux Ubuntu 20.04|
| DVWA-VM1 | VM       | 10.0.0.5   |Linux UBuntu 20.04|
| DVWA -VM2| VM       | 10.0.0.6   |Linux Ubuntu 20.04|
| Elk-VM   | VM       | 10.1.0.5   |Linux Ubuntu 20.04|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 138.91.195.23

Machines within the network can only be accessed by jumpbox.
- jumpbox, IP address 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | YES                 | 10.0.0.1 10.0.0.2    |
| WEB-1    | NO                  | 10.0.0.5             |
| WEB-2    | NO                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It is simple to use and frees up time for the individual.

The playbook implements the following tasks:
- Installs Docker
- Installs python3-pip
- Installs Docker module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![after_ELK_instance](https://user-images.githubusercontent.com/80445107/127472615-6c35c8c5-598b-4465-a10a-d6f50cbd4713.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-  10.0.0.5
-  10.0.0.6
-  10.1.0.5

We have installed the following Beats on these machines:
- Filebeat-7.6.1-amd64.deb
- Metricbeat-7.6.1-amd64.deb

These Beats allow us to collect the following information from each machine:
- Filebeat collects and monitors logs and forwards them to Elasticsearch to stash.
- Metricbeat on the otherhand collects metrics from the operating system and the services its running on the servers. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat.yml file to ELK VM.
- Update the hosts file to include 10.0.0.5, 10.0.0.6, and 10.1.0.5. 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- The playbook is the install-elk.yml file and can found in the directory of /etc/ansible/.
- You need to update the hosts file to be able to run the playbook on a specific machine. You use the sudo docker start command to launch the Elk container.
- http://your.ELK-VM.External.IP:5601/app/kibana 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
# Diagram 
[Diagram]
(Diagrams/Could Diagram.png)
https://github.com/kingdane1/Project-1-ELK-JumpBox/blob/master/Diagrams/Could%20Diagram.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __install-elk.yml__ file may be used to install only certain pieces of it, such as __Filebeat__.


#This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application
Load balancing ensures that the application will be highly , in addition to restricting distribued to the network.
- Load balancers provide servers with security against attacks such as payloads be equally distrubuting traffic across servers on the network. One advantage of using a Jumpbox is to provide initial administrative sercurity when configuring your virtual network while reducing the risks of threats.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __files__ and __system loggs__
- _What does Filebeat watch for?_
__File beat logs files and loactions you specify. it gathers log events__
-  What does Metricbeat record?_
__ from time to time Metricbeat collects metrics from the opersting systems and other running services on the server__

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux(Ubuntu 18.04)  |
| Web-1    | Server   | 10.0.0.5   | Linux(Ubuntu 18.04   |
| Web-2    | Server   | 10.0.0.6   | Linux(Ubuntu 18.04)  |
| Elk-Vm   |Log-Server| 10.1.0.4   | Linux (Ubuntu 18.04) |     

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __Jump Box__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- __the allowed ip addreesses and my personal home IPv4 address__
- 

Machines within the network can only be accessed by __the jump box__ .
- JumpBox: Public IP address (40.83.15.221) && Private IP address (10.0.0.4) 
- the Elk Vm can one be accessed from the Jumpbox
-  __The Jump Box  prive10.0.0.4__

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IPv4 Address    |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
|Elk Server| No                  | My IPv4 Address      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO:__jump box lessens on erros and you can use the jump box to install and configuer all other machines on the network than ssh-in into all of them__

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-__Install docker.io__
- __Install python-pip__
- __Install docker__
- __sysctl module to expand/use more memory__
- __Download and launch the docker container Elk__ 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
#screenshots
![screenshot-docker-ps] (https://github.com/kingdane1/Project-1-ELK-JumpBox/blob/master/Ansible/Docker%20PS.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
- __web-1 10.0.0.5__
- __web-2  10.0.0.6__

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- __filebeat__
- __mertricbeat__

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ (list what file beat and metric bead does)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __configuration__ file in __/etc/ansible/__.
- Update the __host line in the configuration__ file to include __Elk IP____
- Run the playbook, and navigate to __pplaybook__ __Kibana page the the filebeat page to see the data__ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- __filebeat.yml__ is the playbook? Where do you copy it? it is located in  __/etc/filebeat/filebeat.yml__
- _Which file do you update to make Ansible run the playbook on a specific machine? The configuration file
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?
    - __Edit the hont line in the configuration file to add the Elk IP__
- Which URL do you navigate to in order to check that the ELK server is running?
- __http://[elk.ip]:5601/app/kibana.__

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- ssh azureuser@JumpBoxPublicIP
 - ssh-keygen
 - curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > filebeat-configuration.yml
 - curl https://gist.githubusercontent.com/slape/58541585cc1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat > metricbeat-config.yml
 - sudo su
 - Docker start Flamboyant_kepler
 - Docker attach Flamboyant_kepler
 - nano filebeat-configuration.yml
 - nano metricbeat-config.yml
 - nano install-elk.yml
 - nano filebeat.yml
 - nano metricbeat.yml
 - ansible-playbook install-elk.yml
 - ansible-playbook filebeat.yml
 - ansible-playbook metricbeat.yml

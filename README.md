# Projects-
Details on my cloud network

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Red Team Resource Group will be located in. 

Projects-/Diagrams/Azure Red Team Resource Group.png



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  /ansible/ would contain all of the files to create these playbooks.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
The load balancers act as a barrier and allocates traffic evenly so that it does not overload one machine and protects against denial-of-service attacks. What is the advantage to the Jump Box? The advantage to the Jump Box is that it acts as an additional layer of protection to our network by blocking direct access to the public internet and we can allow our machines to access the internet from our private IP’s. This acts as a multi-factor authentication as well as acting as a gateway between the two security zones.   


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jump Box and system network.
What does Filebeat watch for? This application monitors log files and log events.
What does Metricbeat record? Metricbeat collects metrics from the system and services running on the server.  

The configuration details of each machine may be found below.

| Name      | Function   | IP Address | Operating System |
|-----------|------------|------------|------------------|
| Jump Box  | Gateway    | 10.0.0.4   | Linux            |   
| Elk Stack | Monitoring | 10.1.0.4   | Linux            |   
| Web-1     | Hosts      | 10.0.0.5   | Linux            |   
| Web-2     | Hosts      | 10.0.0.6   | Linux            |   


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
71.223.130.92

Machines within the network can only be accessed by SSH. I have set up access for SSH in to Jump Box and HTTP set up through the containers.
The only IP that has SSH access to the Elk server will be 10.0.0.4
 
A summary of the access policies in place can be found in the table below.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Red Team Resource Group:

Projects-/Diagrams/Azure Red Team Resource Group.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to recreate the entire deployment pictured above; alternatively select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  /ansible/ would contain all of the files to create these playbooks.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
The load balancers act as a barrier and allocates traffic evenly so that it does not overload one machine and it protects against denial-of-service attacks. What is the advantage to the jump box? The advantage to the Jump box is that it acts as an additional layer of protection to our network by blocking direct access to the public internet and we can allow our machines to access the internet from our private IP’s. This acts as a multi-factor authentication as well as acting as a gateway between two security zones.   


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump-box and system network.
What does Filebeat watch for? Log files and log events
What does Metricbeat record? Metricbeat collects metrics from the system and services running on the server.  

The configuration details of each machine may be found below.

| Name      | Function   | IP Address | Operating System |
|-----------|------------|------------|------------------|
| Jump Box  | Gateway    | 10.0.0.4   | Linux            |   
| Elk Stack | Monitoring | 10.1.0.4   | Linux            |   
| Web-1     | Hosts      | 10.0.0.5   | Linux            |   
| Web-2     | Hosts      | 10.0.0.6   | Linux            |   


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
71.223.130.92

A summary of the access policies in place can be found in the table below.

| Name          | Publicly  Accessible | Allowed IP Address      | Allowed  Port | Protocols |
|---------------|----------------------|-------------------------|---------------|-----------|
| Jump Box      | Yes                  | Public IP               | 22            | TCP       |
| Load Balancer | Yes                  | Public IP               | 80            | TCP       |
| Elk Stack     | No                   | 10.0.0.4                | 22            | TCP       |
| Web-1         | No                   | 10.0.0.4, 20.98.104.143 | 22 80         | TCP       |
| Web-2         | No                   | 10.0.0.4, 20.98.104.143 | 22 80         | TCP       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because.
The automation functionality benefits the user from having to run tasks manually and allows them to work on more valueable tasks. 

The playbook implements the following tasks:
* The Installation of docker
* Install Python 3 (Python automates and monitors operating systems)
* Increase virtual memory and use more memory, This is becuse it won't operate without running these, because it requires more memory.You must use the sysctl module to automatically run in the event of a system restart.   
* Download and Launch docker elk container. Docker container name= sebp/elk:761
* The container will only run on the following ports that are listed (5601,9200,5044)


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Projects-/Images/Docker_ps_screen_shot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5
10.0.0.6

We have installed the following Beats on these machines:
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat allows us to collect syslogs, sudo commands, SSH logins, user and group information
Metricbeat allows us to collect data from web servers web-1 and web-2 for the following information. CPU, memory, network and disc statistics.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk.yml file to /etc/filebeat/filebeat.yml in your web VM's.
- Update the hosts Playbook file to include. Elk, 10.1.0.4 ansible_python_interpreter=/usr/bin/python3 
- Run the playbook, and navigate to http://20.80.234.117:5601/app/kibana#/home to check that the installation worked as expected.

In order to run the playbook and get updates you will need to run the following command:
ansible-playbook Elk.yml





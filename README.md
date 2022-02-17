# Elk-Server-Project-
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  : /etc/ansible/roles#

This document contains the following details:
- Description of the Topology 
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting latency to the network.


What aspect of security do load balancers protect? They protect DDoS attacks. What is the advantage of a jump box? Jumpbox can act like a backdoor. In addition, adds another layer of security due to it being separated from the other containers in its own security zone.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Data and system logs. 
What does Filebeat watch for? Filebeat monitors the log files or locations that you specify, collecting log events and forwarding them to Elasticseach or Logstash. 

-What does Metricbeat record?_Metricbeat records the metrics and statistics that it collects and ships them to the output you specify. 









The configuration details of each machine may be found below.

_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name              | Function      | IP Address | Operating System |
|-------------------|----------     |------------|------------------|
| JumpBox(RedAdmin) | Gateway       | 10.0.0.7   | Linux            |
| Web1(RedAdmin)    | Webserver1    | 10.0.0.5   | Linux            |
| web2(RedAdmin)    | webserver2    | 10.0.0.6   | Linux            |
| web3(RedAdmin)    | Webserver3    | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 70.106.241.86

Machines within the network can only be accessed by the ansible container.

- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? The jump box machine has access to the Elk VM Ip Address-70.106.241.86

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 70.106.241.86        | 
|  Web1    | No                  | 10.0.0.7             |
|  Web2    | No                  | 10.0.0.7             |    
|  Web3    | No                  | 10.0.0.7             |
|  Elk VM  | No                  | 10.0.0.7             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because service running’s can be limited, and system installation and update can be streamlined: What is the main advantage of automating configuration with Ansible? You can quickly deploy and configure environment, solutions, container, etc. 







The playbook implements the following tasks:
the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Configure Elk VM with Docker
- Install docker.io
- install Docker python module
-Set the vm.max_map_count to 262144
-Download and launch a docker elk container
        

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web3, 10.0.0.8
Web2, 10.0.0.6
Web1, 10.0.0.5

We have installed the following Beats on these machines:
Filebeat and Metricbeat 

These Beats allow us to collect the following information from each machine:

Metricbeat records the metrics and statistics that it collects and ships them to the output you specify. Filebeat monitors the log files or locations that you specify, collecting log events and forwarding them to Elasticseach or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

Copy the ansible.cfg file to /etc/ansible
add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts in the ansible.cfg

Commands:
-nano ansible.cfg
-add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts
-Ctrl + x to exit file
-in the folder that install-elk.yml is in, run: cp install-elk.yml /etc/ansible
nano install-elk.yml /etc/ansible
- name: installing elk hosts: [your_machine]
-Ctrl + x to exit file
-ansible-playbook install-elk.yml

Run the playbook and navigate to Elk server GUI to check that the installation worked as expected.


Answer the following questions to fill in the blanks:_

- Which file is the playbook? Metricbeat-playbook.yml 

Copied: /etc/ansible/metricbeat-config.yml file to /etc/metricbeat/metricbeat.yml


- _Which file do you update to make Ansible run the playbook on a specific machine? The ansible.cfg file. How do I specify which machine to install the ELK. List the correct IP address for each VM in the config file 

server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?http://40.122.167.20:5601/app/kibana#/discover

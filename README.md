# ELK_Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/ZAMINXX/ELK_Project/blob/main/Cloud%20Diagram.PNG 

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

https://github.com/ZAMINXX/ELK_Project/blob/main/Hosts
https://github.com/ZAMINXX/ELK_Project/blob/main/Container-Playbook
https://github.com/ZAMINXX/ELK_Project/blob/main/ELK-playbook
https://github.com/ZAMINXX/ELK_Project/blob/main/Filebeat-playbook
https://github.com/ZAMINXX/ELK_Project/blob/main/Metricbeat-playbook

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

If Web 1 VM goes down Web 2 takes over for it or it can work in reverse if the server is running on Web 2 and it shutsdown Web 1 will take its place. The advantage of using a Jumpbox is that the Jumpbox can only access the Virtual network using SSH. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_ 
Filebeat watches the log files and records them and sends them to Elasticsearch or Logstash
- _TODO: What does Metricbeat record?_
Metricbeat records metrics from your OS and services

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function | IP Address | Operating System |
|-----------|----------|------------|------------------|
| Jump Box  | Gateway  | 10.0.0.4   | Linux            |
| Web 1     | Server   | 10.0.0.5   | Linux            |
| Web 2     | Server   | 10.0.0.6   | Linux            |
| Elk Server| Monitor  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
24.131.148.111

Machines within the network can only be accessed by the Jumpbox.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
The ELK VM can only be accessed through the Jumpbox VM

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 24.131.148.111       |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |
| ELK      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

Not having to go to 3+ machines and input the same commands

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install python3-pip
- Install docker with pip
- Increase Virtual Memory
- Download and launch Docker ELK Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/ZAMINXX/ELK_Project/blob/main/ELK%20Docker%20ps.PNG

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

| Web 1 | 10.0.0.5 |
| Web 2 | 10.0.0.6 |
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat collects log data. Metricbeat collects metrics and statistics. Both send data recorded to Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook (.yml) file to Ansible directory.
- Update the Hosts file to include Web Servers and ELK Server IP
- Run the playbook, and navigate to Kibana to check that the installation worked as expected. (http://[your.VM.IP]:5601/app/kibana)

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

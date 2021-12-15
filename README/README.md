## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. 
Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.

Filebeat monitors system log data.

Metric beat records the machines' metric data.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | DVWA     | 10.0.0.5   | Linux            |
| Web-2    | DVWA     | 10.0.0.6   | Linux            |
| Elk      | Server   | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

98.51.1.63

Machines within the network can only be accessed by 98.51.1.63.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.5 10.0.0.6    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, 
which is advantageous because automtion increases configuration and deployment effeciency of applications.

The playbook implements the following tasks:

-Install docker image and neccessary python libraries using apt modules
-Use pip modules to install docker module and set library dependencies
-Use systemctl command and modules to to increase  virtual memory and use more memory.
-Use docker container module to download and launch docker elk container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/Day1/Capture3

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

-10.0.0.5
-10.0.0.6

We have installed the following Beats on these machines:

-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat collects data on log files, monitoring changes made to them which may be indicitive of events.  Metricbeat collects metric data such as CPU and memory usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the directory with your playbooks.
- Update the hosts file to include the Elk server's ip under "[elk]".
- Run the playbook, and navigate to http://[elk server ip]:5601/app/Kibana to check that the installation worked as expected.


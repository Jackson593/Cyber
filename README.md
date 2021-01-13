# Cyber
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Photos/NetworkDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible Playbook file may be used to install only certain pieces of it, such as Filebeat.

Playbooks/AnsiblePlaybook.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the servers and system.
Filebeat is the first application I installed, it monitors specified logs and reports on any changes.
Metric beat collects and reports periodically on metrics from the system and services running on them.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web 1    | Server   | 10.0.0.5        | Linux            |
| Web 2    | Server   | 10.0.0.6        | Linux            |
| Web 3    | Server   | 10.0.0.8        | Linux            |
| LB          | LB         | 123.96.46.32  | Linux                 |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 76.25.175.8


Machines within the network can only be accessed by using the Jumpbox. 10.0.0.1


A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible         | Allowed IP Addresses             |
|-------------|----------------------------|----------------------------------|
| Jump Box    | Yes/No                     | 10.0.0.1                         |
| Web 1       | No                         | 10.0.0.5                         | 
| Web 2       | No                         | 10.0.0.6                         |
| Web 3       | No                         | 10.0.0.8                         |
| LB          | No                         | 123.96.46.32                     |
| Elk-VM      | No                         | 10.0.0.9                         | 
### Elk Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because it ensures that all the servers are running the services I want them to provide. This task being automated ensures it's always active and upon reboot will ensure all servers are in working order.

The playbook implements the following tasks:
- Install Docker.io, Pythin3-pip, Docker Module
- Increase Virtual Memory and use more memory
- Download and Launch Docker Elk Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4 10.0.0.5 10.0.0.6 10.4.0.1

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat is a service that forwards log data to a centralized location. Files you can typically expect to see would be sys.log files, these typically will include items such as user logins and changes to the system.

Metricbeat is a service quite similar to Filebeat however it monitors for system performance. The types of files you will typically see with it are tmp files that will record the overall system load.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: .

The playbook is the *FILL IN LATER*, it should be copied to /etc/ansible/<file> within the ansible docker.The file needs to be updated as soon at the beginning of this document to reflect the IP addresses of the systems for it to be used on in the hosts file. In order to check the server is running go to http://<IP-Address>/app/kibana

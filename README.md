# Elk Stack project
ELK stack project for UCLA Cyber course
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 ![image](https://user-images.githubusercontent.com/77819150/117171027-5e54ce00-ad7f-11eb-83d5-e51ec75a1ba2.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

Filebeat.yml playbook https://github.com/Armartin7/Cybersecurity_project1/blob/31bac9eb88d56dce9f53490272d5bb26a1c9c3cd/Filebeat.yml%20playbook
Metricbeat.yml playbook https://github.com/Armartin7/Cybersecurity_project1/blob/359e47d5bbc5a1b37cc7bf868e7c72a58687d417/Metricbeat.yml%20playbook

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. The advantage of using a jump box is that access is limited to the people with access to the jump box. The load balancer acts as a way to ensure both web VMs are receiving traffic.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat: monitors the apache log files and locations specified, collects log events, and can forward them to systems like Elasticsearch or Logstash for indexing.
- Metricbeat: is a user friendly, easy-to-use, and efficient metric monitor for your system and the processes running on it.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| ELK      |Log Server| 10.1.0.4   | Linux            |
| Web1     | Server   | 10.0.0.5   | Linux            |
| Web2     | Server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-My Personal IP address

Machines within the network can only be accessed by the Jump Box via ssh.
- The Elk Server gets access through the jump box private IP after accessing the Ansible shell

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses |
|---------------|---------------------|----------------------|
| Jump Box      | Yes                 | personal IP          |
| Elk Server    | Yes                 | 10.0.0.4             |
| Web1          | No                  | 10.0.0.4             |
| Web2          | No                  | 10.0.0.4             |
| Load Balancer | Yes                 | Open                 |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because ansible is user friendly and allowed the making of a playbook which allows configuration of multiple machines with one command given.

The playbook implements the following tasks:
⦁	Install Docker.io
⦁	Install Python3-pip
⦁	Install Docker using pip
⦁	Increase memory of VM
⦁	Download/Launch Docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 ![image](https://user-images.githubusercontent.com/77819150/117170866-3b2a1e80-ad7f-11eb-9554-f913d2bd7c55.png)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
⦁	Web1 (10.0.0.5)
⦁	Web2 (10.0.0.6)
We have installed the following Beats on these machines:
- Filebeat: monitors the apache log files and locations specified, collects log events, and can forward them to systems like Elasticsearch or Logstash for indexing.
- Metricbeat: is a user friendly, easy-to-use, and efficient metric monitor for your system and the processes running on it.
Metric beat can find statistics on SSH Logins, CPU or RAM usage, and times specific machines were accessed to name a few.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the <playbook>.yml file to the Ansible directory.
- Update the host and file to include webservers and ELK (you can pick which to update having these groups)
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

-to run the playbook use the following command <ansible-playbook> <path/to/your/playbook><playbookname.yml> 
After succesful instalation you can send sample data to check your instalation via Kibana to see if it worked you should see the following after accessing
( [your.loadbalancer.IP]:5601/app/kibana )
 ![image](https://user-images.githubusercontent.com/77819150/117170674-12098e00-ad7f-11eb-88fa-4b64620e1e9a.png)

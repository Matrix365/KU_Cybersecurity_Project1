# KU_Cybersecurity_Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

![KU Project 1 Network Diagram Full](13-Elk-Stack-Project/Images/diagram_filename.png)

13-Elk-Stack-Project/Images/Project_1_Network_Diagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

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

Load balancing ensures that the application will be highly available, in addition to restricting external access to the network.
- _TODO: What aspect of security do load balancers protect?  Load balancers protect the network by distributing the traffic to all the devices like multiple web servers so that not all traffic is hitting one web server while the other servers are not having much traffic sent to them.  Load balancers distribute the client requests "equally" across the devices, it ensures high availability and makes the system more reliable and it allows you to easily add or remove devices from the network without disturbing the network. This would be the Availablity in the CIA triad

What is the advantage of a jump box?_ The advantage of a jumpbox is that you minimize your network exposer to the external networks.  Admins connect to the jumpbox system before they connect to internal systems like a web server or other devices.  All Administrators when conducting any Administrative Task will be required to connect to the JumpBox before they perfom any tasks.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system system traffic.
- _TODO: What does Filebeat watch for?_ Filebeat watches for log files/locations and collects log events.
- _TODO: What does Metricbeat record?_ It collects metrics from the operating system and from services running on the server.  Metricbeats can take the metrics and statistics are collected and route them to the output to a system like Elasticsearch or Logstash

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function   | IP Address | Operating System |
|-----------|------------|------------|------------------|
| Jump Box  | Gateway    | 10.0.0.8   | Linux            |
| Web-1     | Webserver  | 10.0.0.10  | Linux            |
| Web-2     | Webserver  | 10.0.0.11  | Linux            |
| Web-3     | Webserver  | 10.0.0.12  | Linux            |
| Elk-VM    | Monitoring | 10.2.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ It was only allowed from my home IP address 68.110.238.18 by SSH

Machines within the network can only be accessed by Jump Box Provisioner.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ I could access the ELK VM by the jumpbox through ssh or I could access it by HTTP from my home machine (68.110.238.18) over port 5601.  I would put the Jumpbox IP whichever it was for the day since it changed by going to http://13.66.252.222:5601/app/kibana was the last address I used.

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses |
|---------------|---------------------|----------------------|
| Jump Box      | Yes                 | 10.0.0.1 10.0.0.2    |
| Web-1         | No                  | 10.0.0.8             |
| Web-2         | No                  | 10.0.0.8             |
| Web-3         | No                  | 10.0.0.8             |
| Elk-Server    | No                  | 10.0.0.8             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Free: Ansible is an open-source tool that allows you to automate numerous types of jobs
- Very simple to set up and use: while it does take some knowledge to correctly set up an Ansible playbook there are resources out on the internet that can be very helpful and some people have playbooks you can use.
- Powerful: Ansible lets you automate jobs that are normally time consumming and even complex task.
- Flexible: You can control the entire application environment. You can customize it to fit your needs for the task you have to perform based on your needs.
- No special software: It does not require you to install any software or agent on a device to automate your task. 
- Efficient: It allows you to use the same playbook on numerous systems and you can get the job done more efficient.
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

Image name is docker_ps_output_sebp-elk761 


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_ 
Web-1 10.0.0.10
Web-2 10.0.0.11
Web-3 10.0.0.12

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Installed filebeat-7.6.1-amd64
https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb

Installed Metricbeats (metricbeat-7.6.1-amd64.deb)
https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.6.1-amd64.deb


These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat - collects data about the file system. It is a system used for forwarding and centralizing log data.
Metricbeat - collects machine metrics, such as uptime.  it collect metrics from your systems and services, including CPU, memory, and much more. It helps keep track of informatio about your system and service statistics.

Example agent hostname provides information like the server that it is getting information from.  Along with the process pid in the example I seen it had process pid 3994.  It would depend on the category that you wanted to look at as to what information you would expect to see.  



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible control node.
- Update the host file to include webserver and elk.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filebeat-playbook.yml
-  Where do you copy it?_ filebeat.yml

- _Which file do you update to make Ansible run the playbook on a specific machine?  Ansible host config file  (/etc/ansible/hosts)
-  How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ You put say for filebeats in a group called Webservers you put the IP addresses of the systems you want to install it on under the Webserver group.  Then for Elk you create a new group and call say ELK and then you put the IP address of the machine there.  Then in the yml file that you have created for the Webserver you tell it to look for the Webserver group.  In the yml file for Elk you tell it to look for the Elk group and it will pull the information from the document. 

- _Which URL do you navigate to in order to check that the ELK server is running?
   http://13.66.252.222:5601/app/kibana


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

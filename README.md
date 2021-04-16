## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Refer to Untitled Diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

 Refer to Filebeat_playbook.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- Load balancers can reduce the load on your web servers and optimize traffic. Load Balancing plays a very important security role as computing every move to the cloud. The off-loading function of a load balancer defends a company or organization against DDos attacks amongst others. It does this by shifting attack traffic from the corporate server to a public cloud provider. The advantage of using a jump box is that the jumpbox is limiting the access to one administator and allowing us to have access to the other VMs and ElK server.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
-What does Filebeat watch for? Filebeat monitors the log files or locations that are specified, collects the log events, and forwards them either to Elasticsearch or Logstash. 


-What does Metricbeat record?_ It periodically collects the metrics from the operating system and from services running on the server. The information the metricbeat collects is usually forwarded to programs such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-VM-1 | DVWA Containers| 10.0.0.3| Linux         |
| Web-VM-2 | DVWA Containers| 10.0.0.4| Linux         |
| Web-VM-3 | DVWA Containers| 10.0.0.5| Linux         |
  ELK-Server Configuration VM 10.2.0.4 Linux

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 My Personal IP

Machines within the network can only be accessed by _____.
-JumpBox-Provisioner
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.4 -Personal IP|
|   Web-VM-1|  No                 | 10.0.0.4                    |
|   Web-VM-2|  No                 | 10.0.0.4                  |
    Web-VM-3   No                    10.0.0.4
    ELK-Server No                   10.0.0.4-JumpBox-PersonalIP/ Port 5601
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible is an open-source tool, very basic coding skills are necessary to use Ansible’s playbook. Ansible allows you to model even highly complex IT workflows.You can customize it based on your needs. You don’t need to install any other software or firewall ports on the client systems you want to automate. Another important aspect is you don’t need to install any extra software, there’s more room for application resources on your server.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
Install docker.io
Install pip3
Install Docker python module
Increase virtual memory
Creates Elk Container
Specificies open ports
- 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Refer to "elk_docker.png"

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring_
Web-VM-1 10.0.0.3
Web-VM-2 10.0.0.4
Web-VM-3 10.0.0.5

We have installed the following Beats on these machines:
Specify which Beats you successfully installed_
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat watches for log files/locations and collect log events
Metricbeat records metrics and statistical data from the operating system and services running on the server
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
Copy the filebeat-playbook.yml file to /etc/ansible/roles
Update the /etc/ansible/hosts file to include the IP address of the Elk Server VM and webservers.
Run the playbook, and go to the Kibana page with http://ELKServerPublicIP:5601/app/kibana# to check that the installation worked.

Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
ELK-Playbook - used to install ELK Server
Filebeat-Playbook - Used to install and configure Filebeat on Elk Server and DVWA servers
Metricbeat-Playbook - Used to install and configure Metricbeat on Elk Server and DVWA servers

and you copy these in /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- etc/ansible/hosts.cfg
- _Which URL do you navigate to in order to check that the ELK server is running?
/etc/ansible/hosts.cfg you have to input your IP address for the specific machine you're installing the ELK server versus the Filebeats.
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

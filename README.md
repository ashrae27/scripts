## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

Playbook1: Pentest yml
![Playbook1 pentest yml](https://user-images.githubusercontent.com/88813019/147843551-9020ef9f-0de3-49f4-9680-34187878a8c7.JPG)

Playbook:ELK yml
![elk_install yml](https://user-images.githubusercontent.com/88813019/148014586-1fb93f1b-0e82-4ab8-8130-647d073e19a7.JPG)

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
- Load balancers protects the VM from DDoS attacks
- The advantage of a jump box gives access to the user and can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_
- Firebeat watches for the log files, locations, and information.
- Metricbeat record metrics and statistics that it collects and ships them to the output.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web1     | Server   | 10.0.0.4   | Linux            |
| Web2     | Server   | 10.0.0.5   | Linux            |
| Web3     | Server   | 10.0.0.6   | Linux            |
| ELK-VM   | Server   | 10.1.0.4   | Linux
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
68.5.26.44 (public IP address)

Machines within the network can only be accessed by JumpBox VM
Which machine did you allow to access your ELK VM? JumpBox
What was its IP address?
 20.120.10.9
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses                 |
|----------|---------------------|----------------------                |
| Jump Box | No                  | 10.0.1.4                             |
| Web1     | Yes                 | 20.124.220.50                        |
| Web2     | Yes                 | 20.124.220.50                        |
| Web3     | Yes                 | 20.124.220.50                        |
| ELK-VM   | No                  | 10.1.0.4                             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?
- Main advantage configuration with Ansible helps with the representation of Infrastructure as code (IAC)

The playbook implements the following tasks:
- Create a new vNet in Azure with the same resource group
- Create a new VM in the new vNet and a minimun of 1 GiB memory
- Create a Ansible playbook installs Docker and put together a Elk container
- Run the playbook to launch the container
- Access to the Elk Vm

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![Elk docker ps](https://user-images.githubusercontent.com/88813019/148014371-0f4fc41f-fc4d-48c8-be57-4e2d1aae9235.JPG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.4
- Web-2: 10.0.0.5
- Web-2: 10.0.0.6

We have installed the following Beats on these machines:
- FileBeat
- MetricBeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
-Filebeat forwarding and monitoring log data or files.
-Metricnbeat collects metrics from the operating system and services running on the server
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk_install file to etc/ansible/.
- Update the hosts file to include...
- Run the playbook, and navigate to HTTP://10.1.0.4:80/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
The commands to run the Ansible for the Elk-VM are:

 -ssh azureuser@20.127.63.165 -i ~/.ssh/elk
- sudo docker container list -a
- sudo docker container start eloquent_booth
- sudo docker container attach eloquent_booth
- cd /etc/ansible/

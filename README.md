# project_1
Submission for Cybersecurity Bootcamp Project 1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Full-Diagram](https://user-images.githubusercontent.com/74391510/134456193-7b517985-4a97-4834-8896-bc7b5cb0e7a2.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - This is the file path from within the container in my Jump Box: /etc/ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_
  - 
  
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the web data and system logs.
- What does Filebeat watch for?
  - Filebeat watches for changes in log data.
- What does Metricbeat record?
  - Metricbeat records system logs.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Webserver| 10.0.0.7   | Linux            |
| Web-2    | Webserver| 10.0.0.8   | Linux            |
| Elk      | Elk Stack| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses
  - 73.20.30.230
  
Machines within the network can only be accessed by the ansible container within the Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address?_
  - I allowed my Elk VM to be accessed by my Jump Box machine with it's private IP address of 10.0.0.4.
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 73.20.30.230         |
| Elk      | No                  | 73.20.30.230         |
| Web LB   | Yes                 | *                    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_
  - With Ansible, you can setup a YAML script to run multiple steps at once when you run the playbook.
  
The playbook implements the following tasks:
- Install docker
- Install python
- Increase and start memory
- Launch docker elk container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![elk container](https://user-images.githubusercontent.com/74391510/134456234-2544c064-da78-4142-b551-34893129f33e.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring.
  - Web-1: 10.0.0.7 
  - Web-2: 10.0.0.8
  
We have installed the following Beats on these machines:
- Specify which Beats you successfully installed.
  - Filebeat and Metricbeat
  
These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see.
  - Filebeat: Responsible for forwarding and centralizing log data; it monitors the log files or locations specified, collects log events, then forwards them for indexing.
  - Metricbeat: Collects metrics from the operating system; it takes the metrics and statistics collected then ships them to the output specified.
  
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-install.yml file to /etc/ansible/roles/elk-install.yml.
- Update the hosts file to include the [elk] attribute, then the destination IP of the Elk server.
- Run the playbook, and navigate to http://20.150.136.144:5601/app/kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.

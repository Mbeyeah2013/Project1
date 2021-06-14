 ## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![My Network Diagram](https://github.com/Mbeyeah2013/Project1/blob/main/Diagrams/Diagram%20(2).png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

[ELK-Install.yml](https://github.com/Mbeyeah2013/Project1/blob/main/Ansible/Install-ELK.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly *available*, in addition to restricting *access* to the network.

- What aspect of security do load balancers protect? #Availability on the CIA Triad#
- What is the advantage of a jump box? #There is only one point of entry so less chance for security breach#

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the *files* and system *usage*.

- What does Filebeat watch for? Monitoring of log files for changes
- What does Metricbeat record? Spikes in system resource use

The configuration details of each machine may be found below.

| Name      | Function    | IP Address | Operating System |
|-----------|-------------|------------|------------------|
| JumpBox   | Entry point | 10.0.0.4   | Linux            |
| Web 1     | logging vm  | 10.0.0.5   | Linux            |
| Web 2     | logging vm  | 10.0.0.6   | Linux            |
| Elkserver | SIEM tool   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- From my public IP: 73.37.198.57

Machines within the network can only be accessed by JumpBox.
- Which machine did you allow to access your ELK VM? The JumpBox
- What was its IP address? 10.0.0.4 / 52.167.2.25

A summary of the access policies in place can be found in the table below.

| Name      | Publically Accessible | IP Addresses             |
|-----------|-----------------------|--------------------------|
| JumpBox   | Yes                   | 10.0.0.4 / 52.167.2.25   |
| Web 1     | No                    | 10.0.0.5                 |
| Web 2     | No                    | 10.0.0.6                 |
| Elkserver | Yes                   | 10.1.0.4 / 40.125.72.159 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible? It can be automated and repeated easily

The playbook implements the following tasks:

- Install Docker.io
- Install Python Module and PIP
- Configure full memory usage
- Install container for ELK
- Set container to run automatically

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker PS](https://github.com/Mbeyeah2013/Project1/blob/main/Diagrams/docker%20ps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web 1 and Web 2 == 10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:

-Filebeat was installed on both machines

These Beats allow us to collect the following information from each machine:

- Filebeat collects log data to process for changes or modification
- Metricbeat collects information of resource usage to see if there is a spike

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the YAML file to files directory.
- Update the hosts file to include a group label and IP address for each machine inside the group
- Run the playbook, and navigate to target machine to check that the installation worked as expected.
- Which file is the playbook? the file that ends in .yml
- Where do you copy it? to the files directory
- Which file do you update to make Ansible run the playbook on a specific machine? the yml file
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? the hosts file and the yml file have a label for the group
- Which URL do you navigate to in order to check that the ELK server is running? the ELK server public IP address

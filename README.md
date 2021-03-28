# PROJECT-13
Automated ELK Stack Deployment - Azure

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram of Azure Virtual Network](Diagrams/Azure_Virtual_Network_II.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.

  ![Filebeat Playbook](Ansible/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting traffic to the network.

- Load balancers address the "availability" aspect of the CIA information security model. They do so by receiving traffic that comes into a website and distributing  it across multiple servers. As websites receive more traffic, more servers can be added to the group or "pool."

- A "Jumpbox" is similar to a gateway router that forces all traffic through a single node making it easier to secure and monitor each individual virtual machines ("VM") behind the gateway.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log and system files.

- "Filebeat" will monitor the VM's by generating and organizing logfiles. It logs information about the file system and specifically provides details about which files have changed and when.

-  "Metricbeat" is a tool that collects metrics or measurements about a system that give an administrator an indication of the systems overall health. Common metrics collected include CPU usage and uptime. .

The configuration details of each machine may be found below.


| Name    | Function | IP Address | Operating System  |
|---------|----------|------------|-------------------|
| Jumpbox | Gateway  | 10.0.0.5   | Linux             |
| ELK     | Monitor  | 10.2.0.4   | Linux             |
| Web-1   | DVWA     | 10.0.0.6   | Linux             |
| Web-2   | DVWA     | 10.0.0.7   | Linux             |
| Web-3   | DVWA     | 10.0.0.8   | Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

 74.165.60.210

Machines within the network can only be accessed by the Jump-Box fromt he following IP address:

- 13.92.230.36

A summary of the access policies in place can be found in the table below.

| Name    | Publically Accessible | Allowed IP Addresses  |
|---------|-----------------------|-----------------------|
| Jumpbox | Yes/SSH               | My Public IP Address  |
| ELK     | Yes/HTTP              | My Public IP Address  |
| Web-1   | No                    | 10.0.0.5              |
| Web-2   | No                    | 10.0.0.5              |
| Web-3   | No                    | 10.0.0.5              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- Ansible is an open-source software provisioning and configuration management software tool. Provisioners do everything from installing software to changing configuration files and has the advantage of avoiding multiple independent entries and accuracy/error avoidance.

The playbook implements the following tasks:

- Install docker.io
- Install Python.pip
- Install Docker (Docker Python pip module)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screenshot of "docker ps" output - Successful configuration of ELK](Linux/Screen_shot_showing_successful_configurationof_ELK_-_sudo_docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

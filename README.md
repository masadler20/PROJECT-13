# PROJECT-13
Automated ELK Stack Deployment - Azure

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram of Azure Virtual Network](Diagrams/NetDiagram.png)

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

-  "Metricbeat" is a tool that collects metrics or measurements about a system that give an administrator an indication of the systems overall health. Common metrics collected include CPU usage and uptime.

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

 - 74.165.60.210

Machines within the network can only be accessed by the Jump-Box from the following IP address:

-  13.92.230.36

A summary of the access policies in place can be found in the table below.

| Name    | Publically Accessible | Allowed IP Addresses  |
|---------|-----------------------|-----------------------|
| Jumpbox | Yes/SSH               | My Public IP Address  |
| ELK     | Yes/HTTP              | 10.2.0.4              |
| Web-1   | No                    | 10.0.0.6              |
| Web-2   | No                    | 10.0.0.7              |
| Web-3   | No                    | 10.0.0.8              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because:

- Ansible is an open-source software provisioning and configuration management software tool. Provisioners do everything from installing software to changing configuration files and has the advantage of avoiding multiple independent entries and accuracy/error avoidance.

The playbook implements the following tasks:

- Install docker.io
- Install Python.pip
- Install Docker (Docker Python pip module)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screenshot of "docker ps" output - Successful configuration of ELK](Linux/Screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web1: 10.0.0.6
- Web2: 10.0.0.7
- Web3: 10.0.0.8

We have installed the following Beats on these machines:
- Filebeats and Metricbeats

These Beats allow us to collect the following information from each machine:

- Filebeats: monitors system logs and events (See Kibana Exploration File)
- Metricbeats: records system metrics and figures including, but limited to, CPU usage, uptime, etc. for the machines being monitored - in this case Web 1,2 and 3. (See Kibana Exploration File)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the Playbook file to /etc/ansible ($ cp /etc/ansible *.yml)
- Update the hosts file to include each VM client IP address (10.0.0.6 10.0.0.7 10.0.0.8)
- Run the playbook, and navigate to 10.2.0.4 and curl localhost/setup.php to check that the installation worked as expected.

Which file is the playbook?

- ansible-playbook.yml (see Ansible folder)

Where do you copy it?

- /etc/ansible

Which file do you update to make Ansible run the playbook on a specific machine?

- It is updated in the hosts file.

How do I specify which machine to install the ELK server on versus which to install filebeat on?

- Add the hosts name elk into the webserver group followed by the IP address for the ELK-SERVER in this case 10.2.0.4 /ansible/hosts.txt

Which URL do you navigate to in order to check that the ELK server is running?

- 13.92.230.36:5601/app/kibana#/home

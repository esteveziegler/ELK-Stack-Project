# ELK-Stack-Project
This project consists of files used to create an automated ELK stack deployment. 

The files in this repository were used to configure the network depicted below.

[Images/diagram_filename.png]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  [yaml files/install_elk.yml]

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems and system metrics.

The configuration details of each machine may be found below.

| Name     | Function      | IP Address | Operating System |
|----------|---------------|------------|------------------|
| Jump Box | Gateway       | 10.0.0.4   | Linux            |
| ELK      | Monitoring    | 10.1.0.4   | Linux            |
| Web-1    | Webserver     | 10.0.0.5   | Linux            |
| Web-2    | Webserver     | 10.0.0.6   | Linux            |
| Web-3    | Load Balancer | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 75.168.207.179
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by each other.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Address |
|----------|---------------------|--------------------|
| Jump Box | Yes                 | 40.86.83.241       |
| ELK      | No                  | 10.1.0.4-254       |
| Web-1    | No                  | 10.0.0.1-254       |
| Web-2    | No                  | 10.0.0.1-254       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible automation helps considerably with the representation of Infrastructure as Code (IAC). Creating an faster and most consistant enviroment, establishing an efficient software development lifecycle, and reduced management overhead.

The playbook implements the following tasks:
    - Install docker.io
    - Install pip3
    - Install Docker python module
    - Increase virtual memory
    - Download and launch a docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web-1 (10.0.0.5) and Web-2 (10.0.0.6)

We have installed the following Beats on these machines: Filebeat, Metricbeat

These Beats allow us to collect the following information from each machine:
    -Filebeat detects changes to the filesystem. Specifically, we use it to collect Apache logs.
    -Metricbeat - Metricbeat detects changes in system metrics, such as CPU usage. We use it to detect SSH login attempts, failed sudo escalations, and CPU/RAM statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to the Ansible Control Node.
- Update the hosts file to include desired webservers and ELK.
- Run the playbook, and navigate to Kibana (http://[Host IP]/app/kibana#/home) to check that the installation worked as expected.

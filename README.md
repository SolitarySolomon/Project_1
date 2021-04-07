## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/SolitarySolomon/Project_1/blob/main/Network%20Diagram%20.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

 https://github.com/SolitarySolomon/Project_1/blob/main/playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
The load balancers help to protect against potential Denial of Service attacks that could be used to damage crucial points of the network.

The jump box provides a hardened and monitored contact point providing access to more sensitive machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system statistics.
 Filebeat sends logs and files to a centralized point to allow easy access to multiple servers, VMs, Etc of logs and 
other important information.
 Metricbeat takes statistics, collects them and sends them to an output of your choice.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address    | Operating System |
|----------|----------|---------------|------------------|
| Jump Box | Gateway  | 40.122.33.156 | Linux            |
| Web 1    | Server   | 10.0.0.9      | Linux            |
| Web 2    | Server   | 10.0.0.8      | Linux            |
| Web 3    | Server   | 10.0.0.10     | Linux            |
| Elk      | Logging  | 10.1.0.4      | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine and the Elk Stack can accept connections from the Internet. Access to these machines is only allowed from the Administrator IP address:


Machines within the network can only be accessed by _Whitelisted IPs_.
I allowed the Jump box access to the Elk server. Jumpbox IP: 40.122.33.156

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Administrator IP     |
| Elk      | Yes                 | Administrator IP     |
| Web 1    | No                  | 40.122.33.156        |
| Web 2    | No                  | 40.122.33.156        |
| Web 3    | No                  | 40.122.33.156        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage of automating the set up the Elk machine and any machine is that it provides
a quick and tested method to simultaneously build multiple machines of the same type providing easy scalability without human error.

The playbook implements the following tasks:
- install docker.io and  pythone3-pip
- install Docker module
- set memory usage
- download and launch elk container
- enable docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/SolitarySolomon/Project_1/blob/main/ScreenELK.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.8, 10.0.0.9, 10.0.0.10

We have installed the following Beats on these machines:

Each Machine has Metricbeat and Filebeat

These Beats allow us to collect the following information from each machine:
Filebeat collects logs and statistics from the servers and sends them to the kibana dashboard providing us with information such as log data and event logs.
Metricbeat gathers the metrics and statistics and sends them to our dashboard in kibana to allow us to see potential unqiue visitors and who might be attempting to gain access.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-install.yml file to your playbooks folder.
- Update the _hosts_ file to include the machine you wish to run the elk playbook on, and place the machine under elk group.
- Run the playbook, and navigate to http://(your Elk servers public IP)/app/kibana#/home to check that the installation worked as expected.

 elk-install.yml is your playbook file and should be placed into where you will be keeping your playbooks
 you will need to update your Hosts file to make ansible run the playback on the machine of your choice. 
you must edit the playbook file to specify which group you want the playbook to install on.
navigate to http://(your Elk servers public IP)/app/kibana#/home to check and see if your installation has worked!

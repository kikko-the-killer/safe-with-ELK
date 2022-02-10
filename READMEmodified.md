{\rtf1\ansi\deff0\nouicompat{\fonttbl{\f0\fnil\fcharset0 Courier New;}{\f1\fnil Courier New;}{\f2\fnil\fcharset2 Symbol;}}
{\colortbl ;\red0\green255\blue255;\red255\green0\blue255;}
{\*\generator Riched20 10.0.19041}\viewkind4\uc1 
\pard\f0\fs22\lang1033 ## Automated ELK Stack Deployment\par
\par
The files in this repository were used to configure the network depicted below.\par
\par
\highlight1 ![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)\par
\highlight0\par
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.\par
\par
\highlight1   - _TODO: Enter the playbook file._\par
\highlight0\par
This document contains the following details:\par
- Description of the Topology\par
- Access Policies\par
- ELK Configuration\par
  - Beats in Use\par
  - Machines Being Monitored\par
- How to Use the Ansible Build\par
\par
\par
### Description of the Topology\par
\par
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.\par
\par
Load balancing ensures that the application will be highly \highlight1 available\highlight0 , in addition to restricting \highlight1 access\highlight0  to the network.\par
What aspect of security do load balancers protect? What is the advantage of a jump box?_\par
\par
\highlight1 Load balancers help ensure that the servers cannot be brought offline, by limiting the potential impact of DDoS attacjs. SPecifically, using a public Cloud provider to load balance ensures that even if an attack transpires -- it does not effect the organization's own resources.\line The jump box creates a centralized entryway into the Virtual Machines we've set up. This is beneficial because of a few reasons\par

\pard{\pntext\f2\'B7\tab}{\*\pn\pnlvlblt\pnf2\pnindent0{\pntxtb\'B7}}\fi-360\li720 There is only one entry way -- so it's easier to monitor \par
{\pntext\f2\'B7\tab}Easier to manage, as new rules must only be applied to the Jump Box\par
{\pntext\f2\'B7\tab}Ease of automation\par
{\pntext\f2\'B7\tab}Network Segmentation\par

\pard\highlight0\par
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the \highlight1 data \highlight0 and \highlight1 system logs\highlight0 . \par
- What does Filebeat watch for?_\par
\highlight1 Filebeat generally reads all the specified data line by line, and forwards it to logstash or KIbana for further analysis. Specifically, a input is responsible for managing the harvesters and finding all sources to read from.A harvester is responsible for reading the content of a single file. The harvester reads each file, line by line, and sends the content to the output.\highlight0\par
- What does Metricbeat record?\par
\highlight1 Metricbeat uses modules and metricsets uses logical sets and operators to collect, fetchh and structure data from a specific service. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. \par
\highlight0\par
\par
- EXTRA: What other beats can be added to this setup and why?\par
\highlight1  Packetbeat - that you can use with Elasticsearch to provide an application monitoring and performance analytics system\par
 Heartbeat - probe services to check if they are reachable or not \f1\emdash  it's useful, for example, to verify that the service uptime complies with your SLA\f0  \par
 Auditbeat - Auditbeat is a lightweight shipper that you can install on your servers to audit the activities of users and processes on your systems. For example, you can use Auditbeat to collect and centralize audit events from the Linux Audit Framework.\line\highlight0\par
The configuration details of each machine may be found below.\par
_Note: Use the [Markdown Table Generator\par
\par
| Name     | Function | IP Address | Operating System |\par
|----------|----------|------------|------------------|\par
| Jump Box | Gateway  | 10.0.0.1   | Linux            |\par
| TODO     |          |            |                  |\par
| TODO     |          |            |                  |\par
| TODO     |          |            |                  |\par
\par
\par
\highlight1 | Name  | Function | IP Address | Operating System |\par
|---|---|---|---|\par
| Jump Box Provisioner | Gateway | 10.0.0.5 | Linux |\par
| Web-1  | Web Server | 10.0.0.10 | Linux |\par
| Web-2 | Web Server | 10.0.0.7 | Linux |\par
| Web-3 | Web Server | 10.0.0.9 | Linux |\par
| Red-ELK-VM | ELK-Server | 10.1.0.6 | Linux |\par
\highlight0\par
\par
### Access Policies\par
\par
The machines on the internal network are not exposed to the public Internet. \par
\par
Only the \highlight1 Red-ELK-VM \highlight0 machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:\par
\highlight1 - The public IP address of admin machine -- 73.96.94.34\highlight0\par
\par
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_\par
\highlight1\par

\pard Machines within the network can only be accessed by ssh through Jumbox and TCP through HTTP -- oirts 22 for ssh and 5601 for TCP.\par

\pard\highlight0\par
\par
A summary of the access policies in place can be found in the table below.\par
\par
| Name     | Publicly Accessible | Allowed IP Addresses |\par
|----------|---------------------|----------------------|\par
| Jump Box | Yes/No              | \highlight1 73.96.94.34\highlight0 |\par
|          |                     |                      |\par
|          |                     |                      |\par
\par
\highlight1 | Name                 | Publically Accessible | Allowed IP Addresses                             |\par
|----------------------|-----------------------|--------------------------------------------------|\par
| Jump Box Provisioner | no                    | 73.96.94.34 though SSH                           |\par
| Web-1                | no                    | 10.0.0.5 through SSH                             |\par
| Web-2                | no                    | 10.0.0.5 through SSH                             |\par
| Web-3                | no                    | 10.0.0.5 through SSH                             |\par
| Red-ELK-VM           | no                    | 73.96.94.34 through HTTP AND 10.0.0.5 though SSH |\par
\highlight0\par
### Elk Configuration\par
\par
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...\par
What is the main advantage of automating configuration with Ansible?\par
\par
\highlight1 Each machine does not have to be manually configured, and an automated process can be created, which will configure a multiutude of machines to the same standard simultaneously. \par
\par
\highlight0\par
The playbook implements the following tasks:\par
- _\highlight2 TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._\par
\highlight0 - ...\par
- ...\par
\par
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.\par
\par
\highlight2 ![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)\par
\highlight0\par
### Target Machines & Beats\par
This ELK server is configured to monitor the following machines:\par
- List the IP addresses of the machines you are monitoring_\par
\tab\highlight1 - Web-1: 10.0.0.10\par
\tab - Web-2: 10.0.0.7\par
\tab - Web-3: 10.0.0.9\par
\highlight0\par
We have installed the following Beats on these machines:\par
-Specify which Beats you successfully installed_\par
\highlight1\tab - Filebeat and MetricBeat\par
\highlight0\par
These Beats allow us to collect the following information from each machine:\par
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._\par
\par
\highlight1     Filebeat: log events\par
    Metricbeat: metrics and system statistics\par
\highlight0\par
### Using the Playbook\par
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: \par
\highlight2\par
SSH into the control node and follow the steps below:\par
- Copy the _____ file to _____.\par
- Update the _____ file to include...\par
\highlight0 - Run the playbook, and navigate to \highlight1 ansible-playbook filebeat-playbook.yml \highlight0 to check that the installation worked as expected.\par
\par
_TODO: Answer the following questions to fill in the blanks:_\par
- _Which file is the playbook? Where do you copy it?\par
\highlight1 There are three playbooks -- one for ansible, one for filebeat and the other for metric beat. They are located in /etc/ansible directory. They are all .yml files\highlight0\par
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?\par
\highlight1 You update the hosts file. You specify what you want installed on a specific machine by \highlight2 ..?\par
\highlight0 - _Which URL do you navigate to in order to check that the ELK server is running?\par
\highlight1 http:// [your.ELK-VM.External.IP]:5601/app/kibana\par
\highlight0\par
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._\par
}
 
ansible-nagios
==============

Nagios is an open source monitoring system for computer systems. It was designed to run on the Linux operating system and can monitor devices running Linux, Windows and Unix operating systems. For example, Nagios can monitor memory usage, disk usage, microprocessor load, the number of currently running processes and log files. it is a powerful monitoring system that enables organizations to identify and resolve IT infrastructure problems before they affect critical business processes. Originally called NetSaint and released in 1999, Nagios was developed by Ethan Galstad and subsequently refined by numerous contributors as an open source project

## What does it do?
   - Automated deployment of Nagios Server on CentOS7 or RHEL7
   - Automated deployment of Nagios client on CentOS6/7/8, RHEL6,7,8, Fedora and FreeBSD
     * Generates service checks and monitored hosts from Ansible inventory
     * Generates comprehensive checks for the Nagios server itself
     * Generates comprehensive checks for all hosts/services via NRPE
     * Generates most of the other configs based on jinja2 templates
     * Wraps Nagios in SSL via Apache
     * Sets up proper firewall rules (firewalld or iptables-services)
     
     
## Requirements
* RHEL7 or CentOS7 for Nagios server only.
* RHEL6/7/8, CentOS6/7/8, Fedora or FreeBSD for the NRPE Nagios client



## How do I manually install Nagiosxi?
* open port 22
* open port 80
* open port 161 for SNMP
* cd /tmp 
* yum install wget 
* wget https://assets.nagios.com/downloads/nagiosxi/xi-latest.
* tar.gz tar xzf xi-latest.tar.gz 
* cd nagiosxi
* ./fullinstall
* Copy and paste IP address into browser 

 ![](/images/Screenshot%20(81).png)
  * welcome page 
  
 
 
 ![](images/Screenshot%20(82).png)
 
 
 ![](images/Screenshot%20(83).png)
 
 
 * fill out login information
 
 
 ![](images/Screenshot%20(85).png)
 
 
 ![](images/Screenshot%20(87)_LI.jpg)
 
 
 ![](images/Screenshot%20(88).png)


 ![](images/Screenshot%20(89).png)
 



 ![](images/Screenshot%20(90).png)


![](images/Screenshot%20(91).png)




## Supported Service Checks
   - Implementation is very simple, with the following resource/service checks generated:
     - Generic out-of-band interfaces *(ping, ssh, http)*
     - Generic Linux servers *(ping, ssh, load, users, procs, uptime, disk space, swap,)*
     - [ELK servers](https://github.com/sadsfae/ansible-elk) *(same as servers plus elasticsearch and Kibana)*
     - Elasticsearch *(same as servers plus TCP/9200 for elasticsearch)*
     - Webservers *(same as servers plus 80/TCP for webserver)*
     - DNS Servers *(same as servers plus UDP/53 for DNS)*
     
    
    
    
    
    
    
    
    
    
    
    
    
    
    
 ![](images/Screenshot%20(92).png)

    
    
    
 
 ![](images/Screenshot%20(93).png)
 
 
 
 
 
 ![](images/Screenshot%20(94).png)
    
    
    
    
    
## Ansible File Hierarchy

```
.
├── hosts
├── install
│   ├── group_vars
│   │   └── all.yml
│   ├── nagios.yml
│   └── roles
│       |
│       └── tasks
│       │       └── main.yml
│       ├── firewall_client
│       │   └── tasks
│       │       └── main.yml
│       ├── instructions
│       │   └── tasks
│       │       └── main.yml
│       ├── nagios
│       │   ├── files
│       │   │   ├── check_ipmi_sensor
│       │   │   ├── idrac_2.2rc4
│       │   │   ├── idrac-smiv2.mib
│       │   │   ├── nagios.cfg
│       │   │   └── nagios.conf
│       │   ├── handlers
│       │   │   └── main.yml
│       │   ├── tasks
│       │   │   └── main.yml
│       │   └── templates
│       │       ├── cgi.cfg.j2
│       │       ├── check_freenas.py.j2
│       │       ├── commands.cfg.j2
│       │       ├── contacts.cfg.j2
│       │       ├── devices.cfg.j2
│       │       ├── dns.cfg.j2
│       │       ├── dns_with_mdadm_raid.cfg.j2
│       │       ├── elasticsearch.cfg.j2
│       │       ├── elkservers.cfg.j2
│       │       ├── freenas.cfg.j2
│       │       ├── idrac.cfg.j2
│       │       ├── ipmi.cfg.j2
│       │       ├── jenkins.cfg.j2
│       │       ├── localhost.cfg.j2
│       │       ├── oobservers.cfg.j2
│       │       ├── servers.cfg.j2
│       │       ├── servers_with_mdadm_raid.cfg.j2
│       │       ├── services.cfg.j2
│       │       ├── supermicro_1028r.cfg.j2
│       │       ├── supermicro_6018r.cfg.j2
│       │       ├── supermicro_6048r.cfg.j2
│       │       ├── switches.cfg.j2
│       │       └── webservers.cfg.j2
│       └── nagios_client
│           ├── files
│           │   ├── bsd_check_uptime.sh
│           │   └── check_raid
│           ├── handlers
│           │   └── main.yml
│           ├── tasks
│           │   └── main.yml
│           └── templates
│               └── nrpe.cfg.j2
├── meta
│   └── main.yml
└── tests
    └── test-requirements.txt

21 directories, 43 files

```

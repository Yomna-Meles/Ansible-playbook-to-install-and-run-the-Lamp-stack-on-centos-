# Ansible-playbook-to-install-and-run-the-Lamp-stack-on-centos-
Playbook starts apache, mariadb and php. Allows traffic on ports 80 and 443 and copies php file from master to client.

Hello there!

In this readme file I will escort you through a simple demonstration on how to create an Ansible playbook to install and run the Lamp stack on centos 7

First things first! Let's start with setting up our environment 

1- Environment Setup:
- Create two centos 7 machines (If you have access to an aws account you could create two instances and follow the same steps) 
- Install ansible on one of the machines and name it master and the other will be the client.

Then let's Yaml! 

2- Yaml file: 
The lamp stack consists of linux apache mysql and php so we will use the yaml file to configure and operate these packages 

2.1 Hosts:
    - You should add you host name (client servers) or name group.
    - If you don't know the host name/ group name then you'll get them from the inventory(hosts) file 
    
    # cd /etc/ansible
    # ls 
    # cat hosts
    
NB: you have to be root user. (errors sparked when i used other users)
2.2 Tasks 
  2.2.1 install and start servicesthis is equivalent yum install in linux host.
  
  2.2.2 I used mariadb here beacuse I faced some error with mysql packages. I will discuss the errors I faced later on.
  
  2.2.3 copy path of php file (in your ansible machine) and add the destination (on host)
  
  2.2.4 Set up firewall rules to allow traffic on ports 80 and 443 (http and https)

Now we are ready. let's head to the ansible machine and deploy our playbook

3- Let's Ansible:
 3.1 create .yml file
   # vi lampstack.yml
    press (i)
   copy yaml and paste it here 
   press esc then save it using (:wq!)

 3.2 deploy!
   # ansible-playbook lampstack.yml 

4- Erros faced: 
  4.1 Calling mysql packages there was a new format but to eradicate errors completely I used mariadb
  4.2 An error in finding the php file kept popping up so make sure of the path. Make sure the file is created under root user beacuse this is what we are using here.

We are all done for now!

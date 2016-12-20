
FOR EXAMPLE GOOGLE_CLOUD and UBUNTU 14.04
=======================

SETUP SERVER FOR CONNECTNG VIA SSH
----------------------

Connected via console to root and create user, for example "deploy"
    
In terminal add
----------------------

- sudo adduser deploy 
- sudo adduser deploy sudo
- su deploy
- sudo visudo 
  - `deploy ALL=NOPASSWD: ALL`
  - `vagrant ALL=(postgres) NOPASSWD:/bin/sh` 
  - (can create for postgres user) 





FOR EXAMPLE AWS and UBUNTU 14.04
=======================

SETUP SERVER FOR CONNECTNG VIA SSH
----------------------

Login to your EC2 instance using your .pem file
----------------------

- `ssh -i your_pem_file.pem ubuntu@ec2-________.compute-1.amazonaws.com`


Create a new user that will access the instance (user will have name "deploy"):
-----
- `sudo useradd -s /bin/bash -m -d /home/deploy  -g root deploy`



Login to your EC2 instance using your .pem file
----------------------

Add user to sudoers file by using sudo visudo and add the following line (sudo visudo):
----------------------

 - `deploy  ALL=NOPASSWD: ALL`



Add ssh key
--------------------- 
  su deploy
  cd ~/.ssh
  ssh-keygen -t rsa -C 'inutero@example.com'


Usage
-----
  - now can connect to server 
    - `ssh deploy@130.211.96.200`
     
1. SETUP ANSIBLE, set parameters of hosts (IP of the server) and var/defaults.yml (IP, name server(deploy), database parameters, version ruby, app name)

Check connection:
  - `ansible -i hosts webserver -m ping -u deploy`
  - (should see green text)

Create environment for remote server
  - `ansible-playbook -i hosts -u deploy server.yml`


Go to application and:
  - `docker-compose run web cap production deploy` 

Authors
=======

Created and maintained by [Oleg Starosvitskij](https://github.com/olegprin)
(oleg.starosvitskij@everprin.com).

License
=======

Apache 2 Licensed. See LICENSE for full details.










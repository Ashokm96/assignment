login into AWS account
click on service next click on EC2
click on instance and click on ubuntu 16.04 LTS
enter number of instance as 2
click on new pair and give some name download key pair
click on lauch instance
1st instance name is MSR-test-Instance-1 and 2nd instance name is MSR-test-Instance-2
open gitbash connect 1st instance and 2nd instance connect with another gitbash
i should established password less ssh between 1st and 2nd instances
open 2nd instance of gitbash following this code
sudo passwd ubuntu
set new password and enter 
cd /etc/ssh
sudo vi sshd_config 
click "i" because insert mode and on file search file password authentication and change it from no to yes
restart ssh i.e sudo service restart
open the 1st instance 
ssh-keygen after enter 3 times because authomatically taken password
ssh-copy-id ubuntu@ip address of 2nd instance
configuration management tool i.e ANSIBLE 
imstall ansible -> sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update --> sudo apt-get install ansible
NVM, Node, Git,and  Docker are installed using ansible
sudo vim /etc/ansible/hosts  --> enter private address of 2nd instance
create ansible playbook for install softwares
vim playbook1.yml   --> pressing i insert mode

---
 - name: testing on local
   hosts: localhost
   become: yes 
   tasks:
    - name: use shell on loc
      shell:
       sudo apt-get update;curl -fsSL https://get.docker.com -o get-docker.sh;
       sh get-docker.sh;
       sudo apt-get update;sudo apt-get install -y nodejs
 
    - name: git module
      apt:
       name: git
       state: present 
 - name: testing on remote
   hosts: all
   become: yes 
   tasks:
    - name: use shell on remote
      shell: 
       sudo apt-get update;curl -fsSL https://get.docker.com -o get-docker.sh;
       sh get-docker.sh; sudo apt-get update;
       sudo apt-get install -y nodejs
    - name: git module
      apt:
       name: git
       state: present
...

and remaining docker compose install by ansible on adhoc commands
sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
gicheck the version of git and docker compose by -->
git --version and docker-compose --version

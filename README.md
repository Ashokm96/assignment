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

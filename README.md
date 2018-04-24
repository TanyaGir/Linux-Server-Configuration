# Linux-Server-Configuration   

Configure a Linux Sever to host a Webapp securely
 
# Server Details
 IP Adress : 18.188.139.111
 
 SSH Port :2200
 
 URL : http://ec2-18-188-139-111.us-east-2.compute.amazonaws.com

# Setup and Configure Instance

1.Create an Amazon AWS Lightsail account.

2.Create a Ubuntu Linux-based instance on Lightsail.

   - Create new instance i.e. my_instance_name on Lightsail.

   - Create and attach a static ip for your Lightsail instance i.e. my_static_ip.

   - Note the Public and Private IPs for your instance, and add the following ports:

     Static/Public IP - Example: 18.188.139.111 
  
     Private IP - Example: 172.26.12.18

3.Click on the 'Connect' tab 

4.Click the 'Account page' at the bottom 

5.Click the 'Download' to download your private key

It should go to your Download folder by default. It is a .pem file.We can use it to log into our server 

6.Click the 'Networking' tab and find the 'Add another' at the bottom

 - Add port 123 and 2200.
 
 # Server Configuration Details
 
 1.Move your downloaded .pem public key file into .ssh folder
 
 2.Going back to your terminal, input 
  - $ chmod 600 ~/.ssh/YourAWSKey.pem
  
3.We now use this key to log into our Amazon Lightsail Server
 - $ ssh -i ~/.ssh/YourAWSKey.pem ubuntu@18.188.139.111
 
4.Amazon Lightsail does not allow you to log in as a root user, but we can switch to become a root user. Type
 - $ sudo su -  and, we become a root user!
 
 # Add user
 - $ sudo adduser grader
 
 # Add user to sudo group
- $ sudo nano /etc/sudoers.d/grader

- Fill that file with grader ALL=(ALL:ALL) ALL, then save it

# Update all currently installed packages
- $  sudo apt-get update

- $ sudo apt-get update

- $ sudo apt-get install finger

# Disable root login
- $ sudo nano /etc/ssh/sshd_config

      Find the PermitRootLogin line and edit to no.
      
- To  enforce the key-based authentication

      Find the PasswordAuthentication line and change text after to no
- After this, restart ssh again

  - $ sudo service ssh restart







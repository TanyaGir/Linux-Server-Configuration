# Linux-Server-Configuration   

Configure a Linux Sever to host a Webapp securely
 
# Server Details
 IP Adress : 18.188.139.111
 
 SSH Port :2200
 
 URL : http://ec2-18-188-139-111.us-east-2.compute.amazonaws.com

# Setup and Configure Instance

1. Create an Amazon AWS Lightsail account.

2. Create a Ubuntu Linux-based instance on Lightsail.

   - Create new instance i.e. my_instance_name on Lightsail.

   - Create and attach a static ip for your Lightsail instance i.e. my_static_ip.

   - Note the Public and Private IPs for your instance, and add the following ports:

     Static/Public IP - Example: 18.188.139.111 
  
     Private IP - Example: 172.26.12.18

3. Click on the 'Connect' tab 

4. Click the 'Account page' at the bottom 

5. Click the 'Download' to download your private key

    It should go to your Download folder by default. It is a .pem file.We can use it to log into our server 

6. Click the 'Networking' tab and find the 'Add another' at the bottom

   - Add port 123 and 2200.
 
 # Server Configuration Details
 
 1. Move your downloaded .pem public key file into .ssh folder
 
 2. Going back to your terminal, input 
 
    - $ chmod 600 ~/.ssh/YourAWSKey.pem
 
 3. We now use this key to log into our Amazon Lightsail Server

    - $ ssh -i ~/.ssh/YourAWSKey.pem ubuntu@18.188.139.111
 
 4. Amazon Lightsail does not allow you to log in as a root user, but we can switch to become a root user. Type
   
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

# Set-up SSH keys for user grader

1. Open a new Terminal window and input

   - $ ssh-keygen -f ~/.ssh/udacity_key.rsa

   - $ cat ~/.ssh/udacity_key.rsa.pub

2. Copy the public key

3. Going back to the first terminal window where you are logged into Amazon Lightsail as the root user, move to grader's folder by

   - $ cd /home/grader

   - $ mkdir .ssh

   - $ touch .ssh/authorized_keys

   - $ nano .ssh/authorized_keys

   - $ sudo chmod 700 /home/grader/.ssh

   - $ sudo chmod 644 /home/grader/.ssh/authorized_keys

   - $ sudo chown -R grader:grader /home/grader/.ssh

   - $ sudo service ssh restart

4. Can now login as the grader user using the command:

   - $ ssh -i ~/.ssh/udacity_key.rsa grader@18.188.139.111

# Disable root login

1. To disable root login

   - $ sudo nano /etc/ssh/sshd_config

         Find the PermitRootLogin line and edit to no.
      
2. Also to enforce the key-based authentication

         Find the PasswordAuthentication line and change text after to no
      
3. After this, restart ssh again

   - $ sudo service ssh restart

# Change timezone to UTC

1. Check the timezone with the date command.

   This will display the current timezone after the time. If it's not UTC change it like this:

   - $ sudo timedatectl set-timezone UTC

# Change SSH port from 22 to 2200

1. First

   - $ sudo nano /etc/ssh/ssdh_config 

2. Then change the line Port 22 to:

    Port 2200

3. Then restart the SSH service

   - $ sudo service ssh restart

4. Disconnect the server by $ ~. and then log back through port 2200: 

   - $ ssh -i ~/.ssh/udacity_key.rsa -p 2200 grader@18.188.139.111

# Configuration Uncomplicated Firewall (UFW)

  - $ sudo ufw allow 2200/tcp

  - $ sudo ufw allow 80/tcp

  - $ sudo ufw allow 123/udp
  
  - $ sudo ufw enable

We will use grader login for the following

# Install Git version control software

  - $ sudo apt-get install git

# Install Apache to serve a Python mod_wsgi application

1. Install required packages

   - $ sudo apt-get install apache2

   - $ sudo apt-get install libapache2-mod-wsgi python-dev

2. Enable mod_wsgi by

  - $ sudo a2enmod wsgi

  - $ sudo service apache2 restart 

  Check for your page at your public IP (18.188.1139.111)

  You should be able to view Apache2 Ubuntu Default Page

3. Set up the folder structure

  - $ cd /var/www

  - $ sudo mkdir catalog

  - $ sudo chown -R grader:grader catalog

  - $ cd catalog

4. Now we clone the project from Github: 

  - $ git clone [your link] catalog 







    







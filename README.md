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

3.Click on the Connect tab 

4.Click the Account page at the bottom 

5.Click the 'Download' to download your private key

   It should go to your Download folder by default. It is a .pem file.We can use it to log into our server 

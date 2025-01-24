AWS-EC2-SETUP-NGINX
🚀 Hosting a Website on Nginx Server on AWS EC2 (Amazon Linux)
This guide will walk you through the process of setting up an Nginx web server on an Amazon EC2 instance running Amazon Linux. By the end, you'll have a simple website hosted and accessible via your public IP address.

🖊️ Prerequisites
Ensure you have the following:

✅ An AWS account and access to the AWS Management Console.
✅ A running EC2 instance (preferably Amazon Linux 2).
✅ SSH access to the EC2 instance using a .pem private key.
✅ Default VPC and Security Group configured.
✅ A Security Group allowing HTTP (port 80) and HTTPS (port 443) inbound traffic.
If you don't have an EC2 instance, create one using the Amazon Linux 2 AMI within the default VPC.

🛠️ Step-by-Step Guide
Step 1: Connect to Your EC2 Instance via SSH
Open a terminal.

Use the following command to connect to your EC2 instance (replace your-key.pem with your private key file and your-ec2-public-ip with your instance's public IP):

ssh -i "your-key.pem" ec2-user@your-ec2-public-ip
For Ubuntu-based instances, replace ec2-user with ubuntu:

ssh -i "your-key.pem" ubuntu@your-ec2-public-ip
Step 2: Update Your EC2 Instance
Update the instance’s package list:

sudo yum update -y
Step 3: Install Nginx
Install Nginx with the following commands:

sudo amazon-linux-extras install nginx1 -y
sudo yum install nginx -y
Step 4: Start Nginx
Start and enable the Nginx service:

sudo systemctl start nginx
sudo systemctl enable nginx
Step 5: Verify Nginx is Running
Check the Nginx status:

sudo systemctl status nginx
You should see Active: active (running) if Nginx is running correctly.

Step 6: Configure Security Group Rules
Allow HTTP (port 80) and HTTPS (port 443) traffic by editing your EC2 instance's Security Group:

Navigate to EC2 > Security Groups in the AWS Management Console.

Select the Security Group associated with your EC2 instance.

Click Inbound rules, then Edit inbound rules.

Add the following:

Type: HTTP, Port Range: 80, Source: Anywhere (0.0.0.0/0)
Type: HTTPS, Port Range: 443, Source: Anywhere (0.0.0.0/0)
Remove any unnecessary inbound rules, such as SSH (port 22), if no longer needed.

Save the rules.

Note: Keep port 22 open if you still require SSH access.

Step 7: Edit the Default index.html
Nginx serves content from /usr/share/nginx/html. Replace the default content:

Navigate to the HTML directory:

cd /usr/share/nginx/html
Edit the index.html file:

sudo vi index.html
Press i to enter insert mode, and replace the content with:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Awesome Website</title>
</head>
<body>
  <h1>Welcome to My Website Hosted on Nginx! 🚀</h1>
  <p>This is a simple webpage hosted on an Amazon EC2 instance with Nginx.</p>
</body>
</html>
Press Esc to exit insert mode.

Save changes and exit by typing :wq and pressing Enter.

Step 8: Restart Nginx
Apply the changes by restarting Nginx:

sudo systemctl restart nginx
Step 9: Access Your Website
Open your web browser.

Enter your EC2 instance’s public IP address:

http://your-ec2-public-ip
You should see the message "Welcome to My Website Hosted on Nginx! 🚀".

✅ Conclusion
🎉 Congratulations! You've successfully set up an Nginx web server on your Amazon Linux EC2 instance. Your website is now live and accessible via the internet.

🚨 Troubleshooting Tips
Nginx isn’t working: Ensure your EC2 instance’s Security Group allows port 80 (HTTP) and port 443 (HTTPS) traffic.
Can’t connect via SSH: Verify your .pem file permissions (chmod 400 your-key.pem).
Website doesn’t load over HTTPS: This guide covers HTTP traffic only. For HTTPS, set up SSL certificates using tools like Let's Encrypt.
AWS-EC2-SETUP-APACHE
🚀 Hosting a Website on Apache Server on AWS EC2 (Amazon Linux)
This guide will help you set up an Apache web server on an Amazon EC2 instance running Amazon Linux. By the end of this tutorial, you’ll have a simple website hosted and accessible via your public IP address.

🖊️ Prerequisites
Ensure you have the following:

✅ An AWS account and access to the AWS Management Console.
✅ A running EC2 instance (preferably Amazon Linux 2).
✅ SSH access to the EC2 instance using a .pem private key.
✅ Default VPC and Security Group configured.
✅ A Security Group allowing HTTP (port 80) and HTTPS (port 443) inbound traffic.
If you don't have an EC2 instance, create one using the Amazon Linux 2 AMI within the default VPC.

🛠️ Step-by-Step Guide
Step 1: Connect to Your EC2 Instance via SSH
Open a terminal.

Use the following command to connect to your EC2 instance (replace your-key.pem with your private key file and your-ec2-public-ip with your instance's public IP):

ssh -i "your-key.pem" ec2-user@your-ec2-public-ip
For Ubuntu-based instances, replace ec2-user with ubuntu:

ssh -i "your-key.pem" ubuntu@your-ec2-public-ip
Step 2: Update Your EC2 Instance
Update the instance’s package list:

sudo yum update -y
Step 3: Install Apache
Install Apache with the following commands:

sudo yum install httpd -y
Step 4: Start Apache
Start and enable the Apache service:

sudo systemctl start httpd
sudo systemctl enable httpd
Step 5: Verify Apache is Running
Check the Apache status:

sudo systemctl status httpd
You should see Active: active (running) if Apache is running correctly.

Step 6: Configure Security Group Rules
Allow HTTP (port 80) and HTTPS (port 443) traffic by editing your EC2 instance's Security Group:

Navigate to EC2 > Security Groups in the AWS Management Console.

Select the Security Group associated with your EC2 instance.

Click Inbound rules, then Edit inbound rules.

Add the following:

Type: HTTP, Port Range: 80, Source: Anywhere (0.0.0.0/0)
Type: HTTPS, Port Range: 443, Source: Anywhere (0.0.0.0/0)
Remove any unnecessary inbound rules, such as SSH (port 22), if no longer needed.

Save the rules.

Note: Keep port 22 open if you still require SSH access.

Step 7: Edit the Default index.html
Apache serves content from /var/www/html. Replace the default content:

Navigate to the HTML directory:

cd /var/www/html
Edit the index.html file:

sudo vi index.html
Press i to enter insert mode, and replace the content with:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Apache Website</title>
</head>
<body>
  <h1>Welcome to My Website Hosted on Apache! 🚀</h1>
  <p>This is a simple webpage hosted on an Amazon EC2 instance with Apache.</p>
</body>
</html>
Press Esc to exit insert mode.

Save changes and exit by typing :wq and pressing Enter.

Step 8: Restart Apache
Apply the changes by restarting Apache:

sudo systemctl restart httpd
Step 9: Access Your Website
Open your web browser.

Enter your EC2 instance’s public IP address:

http://your-ec2-public-ip
You should see the message "Welcome to My Website Hosted on Apache! 🚀".

✅ Conclusion
🎉 Congratulations! You've successfully set up an Apache web server on your Amazon Linux EC2 instance. Your website is now live and accessible via the internet.

🚨 Troubleshooting Tips
Apache isn’t working: Ensure your EC2 instance’s Security Group allows port 80 (HTTP) and port 443 (HTTPS) traffic.
Can’t connect via SSH: Verify your .pem file permissions (chmod 400 your-key.pem).
Website doesn’t load over HTTPS: This guide covers HTTP traffic only. For HTTPS, set up SSL certificates using tools like Let's Encrypt.
🚀 Hosting a Website on Apache Server on AWS EC2 (Amazon Linux and Ubuntu)
This guide will help you set up an Apache web server on an Amazon EC2 instance running Amazon Linux or Ubuntu. By the end of this tutorial, you’ll have a simple website hosted and accessible via your public IP address.

🖊️ Prerequisites
Ensure you have the following:

✅ An AWS account and access to the AWS Management Console.
✅ A running EC2 instance (either Amazon Linux 2 or Ubuntu).
✅ SSH access to the EC2 instance using a .pem private key.
✅ Default VPC and Security Group configured.
✅ A Security Group allowing HTTP (port 80) and HTTPS (port 443) inbound traffic.
If you don't have an EC2 instance, create one using the appropriate AMI within the default VPC.

🛠️ Step-by-Step Guide
Step 1: Connect to Your EC2 Instance via SSH
Open a terminal.

Use the following command to connect to your EC2 instance:

For Amazon Linux:

ssh -i "your-key.pem" ec2-user@your-ec2-public-ip
For Ubuntu:

ssh -i "your-key.pem" ubuntu@your-ec2-public-ip
Step 2: Update Your EC2 Instance
Update the instance’s package list:

For Amazon Linux:

sudo yum update -y
For Ubuntu:

sudo apt update && sudo apt upgrade -y
Step 3: Install Apache
Install Apache using the package manager:

For Amazon Linux:

sudo yum install httpd -y
For Ubuntu:

sudo apt install apache2 -y
Step 4: Start Apache
Start and enable the Apache service:

For Amazon Linux:

sudo systemctl start httpd
sudo systemctl enable httpd
For Ubuntu:

sudo systemctl start apache2
sudo systemctl enable apache2
Step 5: Verify Apache is Running
Check the Apache status:

For Amazon Linux:

sudo systemctl status httpd
For Ubuntu:

sudo systemctl status apache2
You should see Active: active (running) if Apache is running correctly.

Step 6: Configure Security Group Rules
Allow HTTP (port 80) and HTTPS (port 443) traffic by editing your EC2 instance's Security Group:

Navigate to EC2 > Security Groups in the AWS Management Console.

Select the Security Group associated with your EC2 instance.

Click Inbound rules, then Edit inbound rules.

Add the following:

Type: HTTP, Port Range: 80, Source: Anywhere (0.0.0.0/0)
Type: HTTPS, Port Range: 443, Source: Anywhere (0.0.0.0/0)
Remove any unnecessary inbound rules, such as SSH (port 22), if no longer needed.

Save the rules.

Note: Keep port 22 open if you still require SSH access.

Step 7: Edit the Default index.html
Apache serves content from:

Amazon Linux: /var/www/html
Ubuntu: /var/www/html
Replace the default content:

Navigate to the HTML directory:

cd /var/www/html
Edit the index.html file:

sudo vi index.html
Press i to enter insert mode, and replace the content with:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Apache Website</title>
</head>
<body>
  <h1>Welcome to My Website Hosted on Apache! 🚀</h1>
  <p>This is a simple webpage hosted on an Amazon EC2 instance with Apache.</p>
</body>
</html>
Press Esc to exit insert mode.

Save changes and exit by typing :wq and pressing Enter.

Step 8: Restart Apache
Apply the changes by restarting Apache:

For Amazon Linux:

sudo systemctl restart httpd
For Ubuntu:

sudo systemctl restart apache2
Step 9: Access Your Website
Open your web browser.

Enter your EC2 instance’s public IP address:

http://your-ec2-public-ip
You should see the message "Welcome to My Website Hosted on Apache! 🚀".

✅ Conclusion
🎉 Congratulations! You've successfully set up an Apache web server on your Amazon Linux or Ubuntu EC2 instance. Your website is now live and accessible via the internet.

🚨 Troubleshooting Tips
Apache isn’t working: Ensure your EC2 instance’s Security Group allows port 80 (HTTP) and port 443 (HTTPS) traffic.
Can’t connect via SSH: Verify your .pem file permissions (chmod 400 your-key.pem).
Website doesn’t load over HTTPS: This guide covers HTTP traffic only. For HTTPS, set up SSL certificates using tools like Let's Encrypt.
AWS-EC2-SETUP-WEBSERVER-WINDOWS
🚀 Hosting a Website on a Windows EC2 Instance
This guide will help you set up a web server on an Amazon EC2 Windows instance using IIS (Internet Information Services). By the end of this tutorial, you’ll have a simple website hosted and accessible via your instance’s public IP address.

🖊️ Prerequisites
Ensure you have the following:

✅ An AWS account and access to the AWS Management Console.
✅ A running EC2 instance with Windows Server (e.g., Windows Server 2019/2022).
✅ RDP access to your EC2 instance using the private key and administrator credentials.
✅ A Security Group allowing HTTP (port 80) and RDP (port 3389) traffic.
If you don't have an EC2 instance yet, create one with the Windows Server AMI in the default VPC.

🛠️ Step-by-Step Guide
Step 1: Connect to Your Windows EC2 Instance via RDP
In the AWS Management Console, navigate to EC2 > Instances.
Select your Windows instance and click Connect.
Under the RDP Client tab, download the Remote Desktop File and note down the public IP address.
Decrypt the administrator password using your private key file.
Open the downloaded RDP file, enter the administrator credentials, and connect to the instance.
Step 2: Install IIS (Internet Information Services)
Once connected to the instance:

Open Server Manager from the Start Menu.
Click on Manage > Add Roles and Features.
In the Add Roles and Features Wizard:
Installation Type: Select Role-based or feature-based installation.
Server Selection: Select your EC2 instance.
Server Roles: Check Web Server (IIS) and click Next.
Click Next until you reach the Confirmation page, then click Install.
Wait for the installation to complete and close the wizard.
Step 3: Start IIS and Test the Default Website
Open a web browser within the Windows instance.
Enter http://localhost in the address bar.
You should see the default IIS welcome page, indicating that IIS is running.
Step 4: Adjust Security Group Rules for HTTP Traffic
Allow HTTP (port 80) traffic by modifying your instance’s Security Group:

In the AWS Management Console, navigate to EC2 > Security Groups.
Select the Security Group associated with your EC2 instance.
Click Inbound rules > Edit inbound rules.
Add the following rule:
Type: HTTP
Port Range: 80
Source: Anywhere (0.0.0.0/0)
Save the rules.
Step 5: Upload Your Website Files
To replace the default IIS webpage with your own content:

Open File Explorer and navigate to the IIS root directory:
C:\inetpub\wwwroot
Delete or rename the default iisstart.html file.
Copy your website files (e.g., index.html) into this directory.
Step 6: Test Your Website
Open your web browser on your local machine.

Enter your EC2 instance’s public IP address in the address bar:

http://your-ec2-public-ip
You should see your custom webpage.

✅ Conclusion
🎉 Congratulations! You’ve successfully set up a web server on your Windows EC2 instance using IIS. Your website is now accessible via the instance’s public IP address.

🚨 Troubleshooting Tips
Website not loading? Ensure port 80 is open in the instance’s Security Group.
Can’t connect via RDP? Verify that port 3389 (RDP) is open and that you’re using the correct private key and administrator password.
Custom website not displaying? Check that your website files are in the C:\inetpub\wwwroot directory.
# AWS-Journey
Journey of AWS login 

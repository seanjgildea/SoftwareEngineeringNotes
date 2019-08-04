# Setting up AWS CLI

# EC2 Instance setup via CLI

1. Download Secure Shell App for Chrome
2. Find your .PEM file you created when you setup your EC2 Instance
3. Open CMD prompt and navigate to folder the .PEM file is in
4. Run "ssh-keygen -y -f MyKP.pem > MyKP.pub
5. Rename MyKP.pem to MyKP
6. Import both files into the Secure Shell App
7. Specify the EC2 Instance IP address
8. Specify the user name
9. Hit connect
10. Hit yes when prompted to add the list of non-hosts
11. At prompt, type sudo su
12. Type clear 

## Turn EC2 Instance into a Webserver

- yum update -y ( Looks for operating system updates )
- yum install httpd -y ( Install Apache to turn our EC2 instance into a webserver
- cd /var/www/html (Anything you put in here will be a website accessible over port 80 )
- nano index.html ( Write some html code then CTRL+X, then y to save )
- service httpd start ( Turns on Apache Service )
- chkconfig on ( Automatically turns on httpd service if EC2 instance reboots )

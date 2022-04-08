# Hosting-dynamic-application-AWS-RDS-
## Perquisites
- Aws account
- Putty / aws console
- Github Account & Git
- Visual studio code or any ide
- Mysql workbench
- A valid domain or sub domain
## Procedure
### Virtual server setup EC2
1.	Choose a machine image
2.	Choose a Instance type
3.	Confirgure the instance
4.	Add storage 
5.	Add tags 
6.	Configure security group 
7.	Review and launch
### Connect to EC2 using aws console or putty
**In terminal of EC2 run the following commands**
```
Sudo yum update -y 
Amazon-linux-extras
sudo amazon-linux-extras install php8.0
sudo yum install -y httpd
sudo systemctl start httpd
sudo usermod -a -G apache ec2-user
exit
```
***connect to ec2 terminal again***
```
cd /var/www/
sudo chown -R ec2-user:apache /var/www
sudo chmod 2775 /var/www/ && find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;
```
***Setting up git on server and project on it***
```
Sudo yum install git -y
Get personal acess  key from github
Git clone the project on server 
Now lets config the project 
```
### Now lets setup the domain like on godaddy
### Now lets config the appache server
```
cd /var/www/
cd /etc/httpd/conf
ls
sudo nano httpd.conf
```
***At last of the file type  ***
```
# Vhost for http://test.justtolearn.xyz
<virtualHost *:80>
        DocumentRoot "/var/www/html/production_server"
        serverName "test.justtolearn.xyz"
        <Directory /var/www/html/production_server>
        AllowOverride All
        allow from all
        Options +Indexes
        </Directory>
</virtualHost>
```
***And then save it
Move the project folder to http folder 
Now  connect aws rds in project with configerature 
Now git pull on server 
Now create the database and table according to the project requirement..
***

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
![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(185).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(186).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(187).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(188).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(189).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(191).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(192).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(193).png)

### Now lets setup AWS RDS

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(200).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(201).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(202).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(203).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(204).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(205).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(206).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(207).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(210).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(211).png)

***Setting up git on server and project on it***
```
Sudo yum install git -y
Get personal acess  key from github
Git clone the project on server 
Now lets config the project 
```

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(212).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(213).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(214).png)

### Now lets setup the domain like on godaddy

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(215).png)

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

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(216).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(217).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(218).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(219).png)


![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(220).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(221).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(222).png)

![Screenshot](https://github.com/prakash02dec/Hosting-dynamic-application-AWS-RDS-/blob/00f33aa11819d2e6059b04f62660e419f754efa4/images/Screenshot%20(223).png)



```java
#!/bin/bash
yum update -y
yum install httpd -y
service httpd start
chkconfig httpd on
cd /var/www/html
EC2_AVAIL_ZONE=$(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone)
echo "<html><body>IP address of this instance: " >> index.html
curl http://169.254.169.254/latest/meta-data/public-ipv4 >> index.html
echo "<h1>Hello World From Rams at $(hostname -f) in AZ $EC2_AVAIL_ZONE </h1>" >> index.html
echo "<h1>Current Time: $(date) </h1>" >> index.html
echo "</body></html>" >> index.html
```


```java
#!/bin/bash  
yum update -y  
yum install httpd -y  
service httpd start  
chkconfig httpd on  
cd /var/www/html  
echo 'Hello Johnny, Welcome To My Webpage' > index.html  
aws s3 mb s3://johnny-aws-guru-s3-bootstrap-01  
aws s3 cp index.html s3://johnny-aws-guru-s3-bootstrap-01  
```


 ```java
 #!/bin/bash
yum update -y
service mysqld start
chkconfig mysqld on
```


```java
#!/bin/bash
yum update -y
yum install httpd mod_ssl
service httpd start
chkconfig httpd on
```

```java
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` \
&& curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/user-data
#!/bin/bash
yum update -y
service httpd start
chkconfig httpd on
```


# Here is a sample user-data script which sets up an Ubuntu LAMP server on a new EC2 instance:   
```java
#!/bin/bash
set -e -x
export DEBIAN_FRONTEND=noninteractive
apt-get update && apt-get upgrade -y
tasksel install lamp-server
echo "Please remember to set the MySQL root password!"
```


# Running Command Prompt Commands in EC2 User Data
```java
<script>
REM Set timezone
tzutil /s "Singapore Standard Time"
</script>
```

```java
<powershell>
# Install IIS
Install-WindowsFeature -Name Web-Server -IncludeManagementTools
</powershell>
```

# Executing EC2 User Data Every Time Instance Starts

```java
<script>
REM Command prompt commands which will execute every time the instance starts.
</script>
<persist>true</persist>
<powershell>
```

# PowerShell commands which will execute every time the instance starts.
```java
<persist>true</persist>
```


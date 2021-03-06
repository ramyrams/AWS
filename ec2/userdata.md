

```java
#!/bin/bash
yum update -y
yum install httpd -y
service httpd start
chkconfig httpd on
cd /var/www/html
EC2ID=$(curl -s http://169.254.169.254/latest/meta-data/instance-id) 
EC2_AVAIL_ZONE=$(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone)
REGION=$(curl -s 169.254.169.254/latest/meta-data/placement/availability-zone | sed 's/.$//')
IPADR=$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) 

echo "<html><body>" >> index.html
echo "<h1>Rams Test Machine: $(hostname -f) - ($EC2ID)</h1>" >> index.html
echo "<h1>IP Address: $IPADR</h1>" >> index.html
echo "<h1>AZ : $EC2_AVAIL_ZONE </h1>" >> index.html
echo "<h1>Region: $REGION </h1>" >> index.html
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


```java
#!/bin/bash
sudo apt update -y && sudo apt install -y nginx
sudo systemctl start nginx
```


# Install Node and node app
```java
#!/bin/bash
yum update -y
curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
yum install nodejs -y
sudo npm install pm2 -g
pm2 update
cd /home/ec2-user
wget https://github.com/teacheramitk/CRUD-APP/archive/refs/heads/master.zip
unzip master
cd CRUD-APP-master
npm install
pm2 start -f app.js
sleep 10
```

```java
http://publicip:3000/
Security Group TCP 3000
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

# Install have and call the lifecycle-hook
```java
#!/bin/bash

yum update -y && \

sudo yum install java-1.8.0-openjdk-devel && \
INSTANCE_ID="`wget -q -O - http://instance-data/latest/meta-data/instance-id`" && \

aws autoscaling complete-lifecycle-action --lifecycle-action-result CONTINUE --instance-id $INSTANCE_ID --lifecycle-hook-name helloworld-hook --auto-scaling-group-name helloworld-asg --region us-east-1 || \

aws autoscaling complete-lifecycle-action --lifecycle-action-result ABANDON --instance-id $INSTANCE_ID --lifecycle-hook-name helloworld-hook --auto-scaling-group-name helloworld-asg --region us-east-1

# installs only JRE.
sudo yum install java-1.8.0-openjdk 
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


```java
Userdata: Installing IIS on Windows Server 

<powershell> 
Start-Transcript; 

# Install IIS
Import-Module ServerManager; 
Enable-WindowsOptionalFeature -Online -NoRestart -FeatureName 'IIS-WebServerRole', 'IIS-WebServer', 'IIS-ManagementConsole';

# Configure Bindings to :443
New-WebBinding -Name "Default Web Site" -IP "*" -Port 443 -Protocol https -SslFlags 0;
$newCert = New-SelfSignedCertificate -DnsName localhost -CertStoreLocation cert:\LocalMachine\My; 
$SslBinding = Get-WebBinding -Name "Default Web Site" -Protocol "https";
$SslBinding.AddSslCertificate($newCert.GetCertHashString(), "my"); 
Get-WebBinding -Port 80 -Name "Default Web Site" | Remove-WebBinding;

# Install CodeDeploy Agent 
Import-Module AWSPowerShell; 
New-Item -Path "C:\Temp" -ItemType "directory" -Force; 
Read-S3Object -BucketName aws-codedeploy-us-east-1 -Key latest/codedeploy-agent.msi -File c:\temp\codedeploy-agent.msi; 
c:\temp\codedeploy-agent.msi /quiet /l c:\temp\host-agent-install-log.txt;
</powershell>
```

```java
<powershell>
Import-Module ServerManager
tzutil /s "AUS Eastern Standard Time"
Add-WindowsFeature Web-WebServer -includeAllSubFeature -logpath $env:temp\\Web-WebServer_feature.log
Add-WindowsFeature Web-Mgmt-Tools -includeAllSubFeature -logpath $env:temp\\Web-Mgmt-Tools_feature.log
</powershell>

```


```java
<powershell>
Import-Module ServerManager;
Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force
Install-Module -Name AWSPowerShell -Force
#
# Variable Definition
#
$webAppName = "MyWebApp"
$website = "Default Web Site"
$s3Path = "{BUCKET_NAME}"
$zipfileName = "MyWebApp.zip"

$webAppPath = "c:\inetpub\wwwroot\" + $webAppName
$webApplication = "IIS:\sites\" + $website + "\" + $webAppName

#
# Install the Web server Feature of Windows, Including the ASP .NET Features.
#
Install-WindowsFeature Web-Server -IncludeManagementTools -IncludeAllSubFeature
Import-Module WebAdministration;

Read-S3Object -BucketName $s3Path -Key $zipfileName -File "c:\inetpub\wwwroot\$zipfileName"
$shell = new-object -com shell.application
$zip = $shell.NameSpace("c:\inetpub\wwwroot\" + $zipfileName)
foreach($item in $zip.items())
{
    $shell.Namespace("c:\inetpub\wwwroot\").copyhere($item)
}

#
# Set up the web application in the default web site.
#
New-WebApplication -Name $webAppName -ApplicationPool ".NET v4.5" -PhysicalPath $webAppPath -Site $website -force
Set-WebConfiguration system.web/authentication $webApplication -value @{mode='Forms'}
</powershell>
```

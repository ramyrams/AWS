### Install Extra Packages for Enterprise Linux (EPEL)
amazon-linux-extras install epel -y

### install AWS CLI
yum install awscli

### Python pip is the preferred installer program
yum install python-pip awscli -y

### Configure AWS
aws configure
AKIATESTHK7J7UB4GE4O62 
rywTeSTdeJGpSsy+U6E6Mdc7Y7lwrjXFXFW+v
us-east-2

### Create new EC2 instance
aws ec2 run-instances --image-id ami-00dfe2c7ce89a450b --count 1 --instance-type t2.micro --key-name RamsAMSLNX --security-group-ids sg-0514c76c7c8ddb533 --subnet-id subnet-40955a3d





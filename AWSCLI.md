aws --version

aws configure


aws configure --profile produser
aws s3 ls --profile produser

aws configure set region us-west-2 --profile integ
aws configure get region --profile integ
aws configure import --csv file://credentials.csv
aws configure list

aws ec2 describe-instances --profile user1

AWS home directory.

C:\Users\keert\.aws
	config
	credentials
	
How to set environment variables	
C:\> setx AWS_ACCESS_KEY_ID AKIAIOSFODNN7EXAMPLE
C:\> setx AWS_SECRET_ACCESS_KEY wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
C:\> setx AWS_DEFAULT_REGION us-west-2	


aws help
aws s3 help
aws s3 mb help


Create a key pair
 aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem

Display your key pair
aws ec2 describe-key-pairs --key-name MyKeyPair

Delete your key pair
aws ec2 delete-key-pair --key-name MyKeyPair

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





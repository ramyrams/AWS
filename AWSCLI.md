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





**************************************************

14. how to see what are the VPC id's are available
aws ec2 describe-vpcs
15. create security group attached to default VPC network
aws ec2 create-security-group --group-name vijay-ext --description "vijay-ext" --vpc-id vpc-69359312
16.list security groups
aws ec2 describe-security-groups
17. Delete security group
aws ec2 delete-security-group --group-id sg-dcef10aa
18. how to allow ssh traffic to all ip 
aws ec2 authorize-security-group-ingress --group-id sg-be76b5c8 --protocol tcp --port 22 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-id sg-be76b5c8 --protocol tcp --port 22 --cidr 192.168.10.0/24
19.delete the port opened rule only
aws ec2 revoke-security-group-ingress --group-id sg-be76b5c8 --protocol tcp --port 22 --cidr 0.0.0.0/0
20. to list all ami images
aws ec2 describe-images --owners self amazon --filters "Name=root-device-type,Values=ebs"
21. launch the instance
aws ec2 run-instances --image-id ami-00dfe2c7ce89a450b --count 1 --instance-type t2.micro --key-name cnlauth --security-group-ids sg-001aa514a1a4bf841 --subnet-id subnet-89c508e2
23:terminate the instance 
aws ec2 terminate-instances --instance-ids i-0deb3c69be86b230e
24:how to find out instance id
aws ec2 describe-instances --instance-ids
25:to create a glacier storage
aws glacier create-vault --account-id - --vault-name myvault( Note All glacier commands require an account ID parameter. Use a hyphen to specify the current account)
26:creat a bucket 
aws s3 mb s3://vijaycnl1234
27:delete a bicket
aws s3 rb s3://bucket-name
28:to remove a nonempty bucket 
aws s3 rb s3://bucket-name --force
29:to list out buckets
 aws s3 ls
30:to list out specfic buckets
 aws s3 ls s3://bucket-name
31:to delete specfic file in bucket
aws s3 ls s3://bucket-name/path/
32:create a efs storage
aws efs create-file-system \
--creation-token FileSystemForWalkthrough1 \
--region us-west-2 \
--profile adminuser 
33:create a user
aws iam create-user --user-name MyUser
34:add a user yo group
aws iam add-user-to-group --user-name MyUser --group-name MyIamGroup
35:to list out the users in group
 aws iam get-group --group-name MyIamGroup
36:to set a intial password for a user
aws iam create-login-profile --user-name MyUser --password My!User1Login8P@ssword
37:create a acces key for a user
aws iam create-access-key --user-name MyUser
38:to delete a access key for a user
aws iam delete-access-key --user-name MyUser --access-key-id AKIAI44QH8DHBEXAMPLE
39:decribe efs to get file system id
aws efs describe-file-systems \
--region us-west-2 \
--profile adminuser
40:add a tag to efs
aws efs create-tags \
--file-system-id File-System-ID \
--tags Key=Name,Value=SomeExampleNameValue \
--region us-west-2 \
--profile adminuser
41:retrive the tag froom efs
aws efs describe-tags \
--file-system-id File-System-ID \
--region us-west-2 \
--profile adminuser
42:for creating a mount target 
 aws efs create-mount-target \
--file-system-id file-system-id \
--subnet-id  subnet-id \
--security-group ID-of-the security-group-created-for-mount-target \
--region us-west-2 \
--profile adminuser
43:to describe mount targets
aws efs describe-mount-targets \
--file-system-id file-system-id \
--region us-west-2 \
--profile adminuser
44:mounting the efs to ec2
sudo mount -t nfs -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2 mount-target-ip:/  ~/efs-mount-point



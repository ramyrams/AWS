

### Stop Instances
```py
import boto3
region = 'us-east-2'
instances = ['i-09f3821f6364be34f', 'i-045f002a249573ed8']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.stop_instances(InstanceIds=instances)
    print('stopped your instances: ' + str(instances))

```
### Start Instances

```py
import boto3
region = 'us-east-2'
instances = ['i-0435b7ec51de5d697', 'i-0435b7ec51de5d697']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.start_instances(InstanceIds=instances)
    print('started your instances: ' + str(instances))
    
 ```





# Create EC2 Instance
```py
mport boto3
 
AMI = 'ami-087c17d1fe0178315'
INSTANCE_TYPE = 't2.micro'
KEY_NAME = 'DemoEC2'
REGION = 'us-east-1'
 
 
ec2 = boto3.client('ec2', region_name=REGION)
 
 
def lambda_handler(event, context):
 

    instance = ec2.run_instances(
        ImageId=AMI,
        InstanceType=INSTANCE_TYPE,
        KeyName=KEY_NAME,
        MaxCount=1,
        MinCount=1
    )
   
    print ("New instance created:")
    instance_id = instance['Instances'][0]['InstanceId']
    print (instance_id)
 
    return instance_id
 ```

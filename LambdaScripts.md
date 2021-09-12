

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
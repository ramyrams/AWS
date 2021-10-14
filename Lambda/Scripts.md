### Environment Variables
```py

import os
    print("Dynamic Envir : " + os.environ['AWS_REGION'])
    print("Local Envir : " + os.environ['MyName'])
```
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
 
 
 ## Simple hello world - adding two numbers
 ```py
 
 from __future__ import division

def lambda_handler(event, context):
   number1 = event['Number1']
   number2 = event['Number2']
   sum = number1 + number2
   product = number1 * number2
   difference = abs(number1 - number2)
   quotient = number1 / number2
   return {
       "Number1": number1,
       "Number2": number2,
       "Sum": sum,
       "Product": product,
       "Difference": difference,
       "Quotient": quotient
   }
   
```
   
```json   
{
   "Number1": 10,
   "Number2": 20
}
```



def my_handler(event, context):
   return "aws lambda in python using zip file"


def my_handler(event, context):
   print("Log stream name:", context.log_stream_name)
   print("Log group name:",  context.log_group_name)
   print("Request ID:",context.aws_request_id)
   print("Mem. limits(MB):", context.memory_limit_in_mb)
   print("Time remaining (MS):", context.get_remaining_time_in_millis())
   return "aws lambda in python using zip file"


client_context.client.installation_id
client_context.client.app_title
client_context.client.app_version_name
client_context.client.app_version_code
client_context.client.app_package_name
client_context.custom - it has dict of custom values from the mobile client app
client_context.env - it has dict of environment details from the AWS Mobile SDK



def my_handler(event, context):
   print("Log stream name:", context.log_stream_name)
   print("Log group name:",  context.log_group_name)
   print("Request ID:",context.aws_request_id)
   print("Mem. limits(MB):", context.memory_limit_in_mb)
   print("Time remaining (MS):", context.get_remaining_time_in_millis())
   return "aws lambda in python using zip file"



import logging
logger = logging.getLogger()
logger.setLevel(logging.INFO)
def my_handler(event, context):
   logger.info('Using logger to print messages to cloudwatch logs')
   return "aws lambda in python using zip file"




def error_handler(event, context):
   raise Exception('Error Occured!')


exports.handler = function(event, context, callback) {
   console.log("Incoming Event: ", event);
   const bucket = event.Records[0].s3.bucket.name;
   const filename = decodeURIComponent(event.Records[0].s3.object.key.replace(/\+/g, ' '));
   const message = `File is uploaded in - ${bucket} -> ${filename}`;
   console.log(message);
   callback(null, message);
};



exports.handler = function(event, context, callback) {
   console.log("Incoming Event: ", event);
   const bucket = event.Records[0].s3.bucket.name;
   const filename = decodeURIComponent(event.Records[0].s3.object.key.replace(/\+/g, ' '));
   const message = `File is uploaded in - ${bucket} -> ${filename}`;
   console.log(message);
   callback(null, message);
};



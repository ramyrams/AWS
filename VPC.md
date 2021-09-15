VPC
While creating if you are selecting dedicate network it costly because they configure firewall and high priority.

Create VPC
Services -> VPC -> Create VPC -> select default and create network
Check the Routing table you can see only default
Create internet Gateway and its detached by default
Right click the internet gateway which you created -> Attach VPC -> Select VPC which you created on 1st step
Subnet don’t touch the default subnet, create a new one (as per 6 and 7th points)
Create subnet -> chose VPC and -> and select 1st AZ- and their subnet which you want to release. create subnet --> create public subnet --> 10.0.1.0/24
Create Subnet -> choose VPC and -> and select 2nd AZ- and their subnet which you want to release. Create subnet --> create private subnet --> 10.0.2.0/24
Right click 1st subnet which need enable public auto assign IP address to EC2 instance
Create two routing table for 1 network public and 2nd network private
Edit the routes for both the routing table and add 0.0.0.0/0 ad choose the gateway which we created on 4th step
Select Public Routing table (1nd routing table which we created and edit subnet associate and choose 10.0.1.0/24 network
Create 1st instance with 1st subnet see public ip will automatically enable and assign, so that instance will be in public (security group enable http, https and icmp for all the IP)
Create 2nd instance with 2nd subnet see public ip will not enable its disable by default, so that instance will be in private it’s not participating in public (Security group and enable http, https, icmp for only 10.0.1.0 network
Create 3rd instance from community AMI -> search NAT and choose 1st image, and choose 1st network which public and 10.0.1.0/24 network
Right click the 3rd NAT image -> Networking -> Disable change source/destination check.
Edit the private network routing table or 10.0.0.0/16 (Seems I have missed to configure major network) edit the routes and remove gateway of 0.0.0.0/0 and choose 3rd instance id.
---
- name: deploy nginx
  host: all
  tasks:
    - name: install

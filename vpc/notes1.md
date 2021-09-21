FAQ: https://aws.amazon.com/vpc/faqs/

IRC 1918 standard
10.0.0.0/16
172.16.0.0/16
192.168.0.0/16

CIDR Notiation
16 bit alocated for network
last 16 bit allocated for resources

10.0.0.0/16

Start 10.0.0.0
End 10.0.255.255
256*256 IP address
Total IP Count: 2^(32-16) = 65536
Range: 10.0.0.0 to 10.0.255.255

AWS Reserves 
10.0.0.0: Network address.
10.0.0.1: Reserved by AWS for the VPC router.
10.0.0.2: Reserved by AWS. The IP address of the DNS server is the base of the VPC network range plus two. 
10.0.0.3: Reserved by AWS for future use.
10.0.0.255: Network broadcast address. We do not support broadcast in a VPC, therefore we reserve this address.


Max Supported: 10.0.0.0/16
Min Supported: 10.0.0.0/28


VPV is your virtual network in AWS Clud isolated fro other AWS customers
Full control over your VPC(Network, security, etc)
1 VPV for 1 region
1VPC can have multuple subnet
1 submnet for 1 AZ
1 subnet must be assioated with 1 route table
Route table can have multiple associatged subnets
Routing inside the VPC is always possible with VPC router


VPC constructs
IP address range (CIDR Block)
VPC router
Route Table
Internet Gateway
Security Groups
Network ACL
Virtual private Gateway

Max CIDR range for VPC is /16 (65536 IP Address)

Min CIDR range for VPC is /28 (16)IP Address)

Subnet within VPC can't have overllapping IP ranges
AWS reserver 4 IP Address from CIDR Range
You can't chagne or modify CIDR block of your VPC after creation
YOu can extent your VPC CIDR block

VPC resources can talk to internet via internet Gateway (IGW)
Ineternet Gateway is a fully managed, higly scalable service.
It performs network address transulation (Private <-> Private)



We have two securityconstrcut for VPC
NACL 
Security Groups

Elastic network Interface (it is vitirual network interfact attached to virutual machine)

Security groups operates at ENI of the instance
Secutity groups are vitural firewall
THere allow or block traiffic in and out of the EC2 instance
EC2 instance can have up to 5 security group
Secuity groups are stateful
Cam have only allow rules
If no rule is defined in the SG, traffic is blocked to the instance


NACL operates at subnet level, gatekeep of the submet
NACL are stateless
BOth allow and deny rules are possible
NACL rules evalued from lower numner to hight number
Lower ril number, hight the priority
NACL rules are applied to all the instance within the subnet







Tool:
https://www.ipaddressguide.com/cidr



VPC - Ireland
10.0.0.01/16
Range: 10.0.0.0 - 10.0.255.255
Total IP: 65???

Subnet01-AZ1 
Named as public Subnet
10.0.0.0/24
Range: 10.0.0.0 - 10.0.0.255
Total IP: 256

Subnet02-AZ2
Nameed as private Subnet
10.0.1.0/24
Range: 10.0.1.0 - 10.0.1.255
Total IP: 256

Add Webserver in Subnet01
IP: 10.0.0.8

Add DB Server in Subnet02
IP: 10.0.1.15

Add Route Table (Subnet 01)
10.0.0.0/16 local
0.0.0.0/0 inetnet gatewayid

Add ROute Table (Subnet 02)
10.0.0.0/16 local
0.0.0.0/0 nat-gateway-id

Add Internet gateway for subnet0q

NAT Gateway








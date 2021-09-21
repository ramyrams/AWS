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


Tool:
https://www.ipaddressguide.com/cidr


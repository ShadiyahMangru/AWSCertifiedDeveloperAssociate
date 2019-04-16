# AWS Certified Developer -- Associate
Notes in Preparation for Exam DVA-C01

## AWS Fundamentals: IAM + EC2

- IAM Federation:
   -	used by big enterprises to integrate own active directory with IAM
   -	uses SAML standard
- IAM:
   -	global service (no need to select a region)
   -	manage user access and encryption keys 
   -	one IAM USER per physical person
  -	one IAM ROLE per application
- never use ROOT account, except for initial setup – create an alias account for daily use
- Activate virtual MFA with Google Authenticator
- Give yourself (user) admin access
- EC2:
   -	launch VMs in cloud (virtual servers in cloud)
   -	choose Amazon Machine Image (AMI) – the software and OS that will be launched on that server
   -	use Amazon Linux 2
   -	choose type to specify memory
- EBS – store data on virtual drives (to store OS of EC2 instance)
- ELB – distributing load across machines
- ASG – scaling services using an auto-scaling group
- EC2 security group – a firewall around your instance
- SSH source 0.0.0.0/0 means your security group open to the world
- Create key pair to access launched EC2 instance
- Instance state: start/stop/reboot/terminate
- SSH (port 22):
   -	allows you to control a remote machine, all using CLI (from a terminal)
   -	use Putty from a Windows machine (Putty Key Generator for .ppk file)
- Security Group
   -	to control inbound/outbound traffic through ports to/from EC2 instance
   -	to control authorized IP ranges – IPv4 and IPv6
   -	all outbound traffic authorized by default
   -	can be attached to multiple instances
   -	specific to region and VPC combination
   -	application time out: security group issue
   -	“connection refused” error: application error or instance not launched
- Internet Gateway – public gateway (to connect private machines to www)
- With private IP:
   -	only accessible within private network
   -	IP must be unique across private network (not necessarily unique across entire www)
   -	Only a specified range of IPs can be used as private IPs
- Elastic IP:
   -	To ensure IP for your instance is fixed
   -	With elastic IP address, can mask failure of an instance or software by rapidly remapping the address to another instance in your account
- Recommend avoid elastic IP and use (i) a random public IP and register DNS name to it or (ii) load balancer and no public IP
- If EC2 instance stopped then started, PUBLIC IP can change (if elastic IP NOT associated with the instance)

...

## Sources
- Ultimate AWS Certified Developer Associate 2019 (Udemy for Business)

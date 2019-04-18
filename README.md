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
   -	“connection refused” error: application error or instance not launched (https://aws.amazon.com/premiumsupport/knowledge-center/ec2-server-refused-our-key/)
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

- section 3, video 20 to install an Apache Web Server to display a web page
- section 3, video 21  to create webpage via automated boot tasks / EC2 user data script (activate SSH, http, and https in security groups to avoid connection timeout)
- EC2 instance launch types:
   - on demand
   - reserved (recommended for steady state usage applications -- e.g., database)
   - convertible reserved instances (can change EC2 instance type)
   - scheduled reserved instances
   - spot (bid) -- instance lost when outbid
   - dedicated instances -- no other customers will share your hardware
   - dedicated hosts -- often for strong regulatory or compliance needs
<br>

## AWS Fundamentals: ELB + ASG + EBS
### ELB:
- high availability across zones
- ELB: managed load balancer
- application load balancer to balance multiple applications on same machine (ex. containers)
- classic load balancers -- deprecated
- application load balancers -- http/https and websockets
- network load balancer -- TCP
- all load balancers have health check capability
- with load balancer, assigned a DNS.  if have an EC2 instance with an IP address (an IP that may not be fixed), can use load balancer to register this EC2 instance as a target EC2 instance and configure the security group associated with that EC2 instance so that incoming (port 80) traffic ONLY COMES FROM LOAD BALANCER.  Now only reach .html info from that EC2 instance from load balancer DNS address (can no longer access from EC2 instance IP (maybe unfixed) address)
- with Load Balancers, enable stickiness so user's don't have to reauthenticate when switch pages/instances

### ASG:
- IAM roles attached to an ASG will get assigned to EC2 instances
- when creating an ASG, step 1 creates launch config (incl. user data for boot instructions)
- $(hostname -f) on echo line (of user data script) will display address of different instances to which load balancer routing

### EBS:
- a network drive
- can attach to instances while they're running
- detachable but locked to an AZ
- resizable
- snapshots (i) to backup and (ii) for volume migration (to recreate EBS volume in another AZ)
- when EBS volume encrypted, get (i) encrypted data at rest, (ii) encrypted data in flight, (iii) all snapshots encrypted, (iv) all volumes created from snapshots are encrypted
- instance store -- EBS volumes that do not come with root (therefore on termination, instance store lost)

<br>

## Sources
- Ultimate AWS Certified Developer Associate 2019 (Udemy for Business)

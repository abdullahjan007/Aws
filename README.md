# Aws (Amazon Web Service)
# DAY 01<br></br>
# What is cloud?<br></br>
Before 20 years, what happened? Organizations buy servers to deploy their applications on the servers. Similarly, like you buy a laptop, install a software in your laptop and then use it. 
So, companies go to ibm, hp or other cloud provider and purchase some 15-20 servers from them and create the datacenter (Datacenter is a place where servers are present with proper configuration, network, temperature etc) and at that time there isn’t any concept of virtualization so what happened? One application is deployed on one server which leads to a resources wastage because server consist of 100GB and 100CPUs but application is of 1GB only and the next time when another application is developed it is deployed on the next server. So, a concept of virtualization comes in and one server is divided into multiple virtual servers and applications are deployed on the virtual server with a single base server. 
Now with the concept of virtualization we can create virtual machines at any part of the world and share their IPs with the other people so they can use it. So, that’s why this concept is called a cloud means they are interconnected I am using the servers without knowing where they are. And who is managing this entire thing? Ans is system administrator. When we do this thing entirely in our organization that’s why we call it private cloud because we use it entirely in our organization. No one from external organization come and use our instance/virtual server. (On-prem data centers)
Amazon and Microsoft saw this as an opportuninty because for a startup, even for a mid-level organization it is difficult to manage servers, their temperature, configurations and other things so aws, Microsoft ask them no problem we can do this for you you just have to purchase/rentout the instances from us. So, this type of cloud is a public cloud where anyone from the world can use the instances. We can also create Virtual Private Cloud in a Public Cloud we will see it later.
<br></br>
# Q: Why Public Cloud is so Popular?<br></br>
A: As we said, it saves the cost and maintenance overhead.
Companies don’t want to dedicate a team for server mainetenance and aws, Microsoft is a pay to go services. 
Initially aws have only ec2 instances/servers, then they provide databases services as well. 
Ab jaisey hi koi cheez popular market may ati ha aws us ki services provide kr deta ha. Let say, it is difficult to setup a kubernetes cluster so what you do? You simply go to aws and ask him give me the kubernetes cluster with 4 nodes.
<br></br>
# Q: Why aws is better than other?<br></br>
A: aws is the cloud pioneer and it takes the early advantage. People uses it at very start and now a days it takes the maximum market share.
<br></br>
# Q: Are people moving away from cloud?<br></br>
A: Moving from private cloud to public cloud is called cloud repatriation. Initially people move from private cloud to public cloud and then some people again moving back from public cloud to private cloud (but these percentages are very small).

# DAY 2 IAM(Identity and Access Management) User:<br></br>

Let suppose, a bank have employee desk, help desk, security desk, lockers area etc. So, when someone enter in a bank there must be authentication and authorization mechanism. Like at the gate he first must be authenticated (like either a person has an account in a bank or he is the employer in the bank or he has some work in the bank jaisey guard gate pay hum say pochta ha kay kia kaam kia ha aur hum btatey hain kay bill jama karwana ha phir wo humey ander janey deta ha) after authentication we enter in the bank and then authorized to the associated department like if we are employer we authorized to the employee dept, locker area and so on… Now imagine if there isn’t any authorization and authentication mechanism, then anyone can enter into the bank and rob the bank. Same is the concept of IAM user. 
Let suppose you are working in an organization and as a devops engineer your responsibility is to create<br></br>
aws account. You create a root user account with some services like EC2, database, S3 and so on. After some time a new employee came and ask me to give him access to the companies aws account and when I give him the root access then there might be a chance kay wo database intentionally or unintentionally delete kr de so what I can do..i ask him kay tumhey kon kon si services ki zaroorat ha and let suppose he say I want to read datatbase and ec2 so I go and create an iam user in which I set the policy to give him database read access and ec2 access after that I share those iam creadentials with him. So in this way he is first authenticated when he adds the credentials to login and then authorized to use the only services that I mentioned in the policy.<br></br>
# IAM have 4 things<br></br>
User, Policies, Groups and Roles..i will explain each of this in following:<br></br>
First disucuss user.. At first when some employee said give me the access to company aws so you first create its’s iam user and for every user you must have to set policies. If policies are not set then iam user is not authenticated or authorized because he don’t know what to do next or which service to use so you must need to set policy for the user. Now discuss groups. See, in a company multiple people are leaving and multiple new people are coming so it is very time taking kay every time you have to create user and attach policies for the multiple new comings or leavings. So, what you can do you create a groups. Let suppose in your company you have 1 group of developers, 1 group of testers, 1 group of Designers etc. When a new people is hired you just ask him kay which group you belong he said I am from developer team so you create its iam user in developer group where policies are set or you just add him in developer group. (Users give authentication and policies gives authorization) (Must use a IAM account instead of root user account. Even if you are DevOps engineer then still use the IAM account with most of the access) <br></br>
# Now discuss about Roles:<br></br>
Role is a temporary set of permissions that AWS services or users can “assume” to do a job securely without passwords. 🔐<br></br>
Roles are mostly related to user but not similar to user. Roles have temporary username and password unlike user which have permanent username and password. Roles are usually used for the external communication like it is used for the services running outside aws (as per my understanding I am not sure about it). If there are two aws accounts and we want to talk between these 2 aws accounts then we use Roles. Let’s take a scenario:<br></br>
Let suppose developer create an application but he don’t use the on prem database instead he use the database services on cloud and his application is present on private cloud (same scenario jo Ibrahim nay kia tha medical cloud waley project may…jb us nay qdrant db use ki thi). Now when a customer wants to use the application.. application takes data from the aws database and give it to the user and this data fetching work is done through roles.

# CHATGPT OVERVIEW:<br></br>
An IAM Role is like a temporary permission badge in AWS.<br></br>
👉 No username<br></br>
👉 No password<br></br>
👉 Used temporarily<br></br>
________________________________________<br></br>
# Easy definition 🌱<br></br>
IAM Role = Permissions without a permanent user<br></br>
Instead of who you are, a role defines what you are allowed to do for a short time.<br></br>
________________________________________<br></br>
# Real-life example 🎟️<br></br>
Example: Hotel Key Card<br></br>
•	Hotel = AWS<br></br>
•	Rooms = AWS services<br></br>
•	Key card = IAM Role<br></br>
When you check in:<br></br>
•	You get a temporary key card<br></br>
•	It works only during your stay<br></br>
•	It expires automatically<br></br>
You don’t create a new employee just to stay one night — same idea with roles.<br></br>
________________________________________<br></br>


# Why IAM Roles are needed ✅<br></br>
Using passwords or access keys:<br></br>
•	Can be leaked<br></br>
•	Are hard to rotate<br></br>
IAM Roles:<br></br>
✅ No stored keys<br></br>
✅ Temporary access<br></br>
✅ More secure<br></br>
________________________________________<br></br>
# Common Simple Scenarios 🧠<br></br>
1️⃣ EC2 instance needs S3 access<br></br>
Instead of:<br></br>
•	Creating IAM user<br></br>
•	Storing keys on server ❌<br></br>
Do this:<br></br>
•	Create IAM Role with S3 permission ✅<br></br>
•	Attach role to EC2<br></br>
👉 EC2 automatically gets temporary access<br></br>
________________________________________<br></br>
2️⃣ Employee temporarily needs admin access<br></br>
•	Normal access: Developer<br></br>
•	For 1 hour: Admin<br></br>
Give:<br></br>
•	Role with admin permissions<br></br>
•	Role expires after session<br></br>
✅ No password sharing<br></br>
________________________________________<br></br>
3️⃣ One AWS account accessing another<br></br>
•	Account A needs access to Account B<br></br>
•	Use role assumption<br></br>
Think of it as borrowing keys, not owning them.<br></br>
________________________________________<br></br>
# Simple technical example 🔧<br></br>
IAM Role Policy (what it can do)<br></br>
{<br></br>
  "Effect": "Allow",<br></br>
  "Action": "s3:GetObject",<br></br>
  "Resource": "*"<br></br>
}<br></br>
✅ Allows reading files from S3<br></br>
❌ Cannot delete or create files<br></br>
________________________________________<br></br>
Trust Policy (who can use the role)<br></br>
{<br></br>
  "Effect": "Allow",<br></br>
  "Principal": {<br></br>
    "Service": "ec2.amazonaws.com"<br></br>
  },<br></br>
  "Action": "sts:AssumeRole"<br></br>
}<br></br>
🧠 Meaning:<br></br>
•	EC2 is trusted<br></br>
•	EC2 can use this role<br></br>
•	Nobody else can<br></br>

# DAY 3 EC2(Elastic Cloud Compute):<br></br>

# Q: What is an EC2 instance?<br></br>
EC2 (Elastic Cloud Compute) as name suggest that we are requesting aws to give us a compute which is a combination of CPU, RAM and disk inshort we request aws to give us a virtual server. <br></br>
Let suppose I am using a laptop and now I want kay my laptop is used by 2-3 more people so what I can do..i simply install hypervisor on my laptop and create a 2-3 virtual server/env now my laptop is used by 2-3 people other than me..Laptop is very small thing, servers are very expensive. So, usually people buy one server and multiple virtual servers are created on top of it and people use it with the help of hypervisor. Same goes for aws. Aws has a large datacenter across the world. When we ask aws to give me a ec2 means virtual server at specific region then what happened? My request is go to aws hypervisor and then aws assigned us an instance of ec2. (Not cnfrm)<br></br>
We noticed that some of the aws services have a prefix Elastic. What this prefix mean? The services that can be scaled up or scaled down based on usage are usually named with a prefix Elastic i.e EKS, EBS, EC2.<br></br>

# Q: Why we should use an EC2 instance?<br></br>
To reduce the maintenance overhead. Let suppose as a devops engineer my task is to create a virtual machines for 100 developers so what I can do? First purchase a server then do the configuration and assigns VM to a developers but after this a dedicated team is needed for maintenance but with the help of Public Cloud. This type of things are done by cloud provider itself. AWS EC2 is a pay to go service means I can only for those time when I use the server. If at night I usually don’t use the server then there isn’t any need to pay.. simply close the EC2 instance and done. Also due to Elastic feature we can easily scaled up or scaled down the instance according to our need.<br></br>

# Types of EC2 instances:<br></br>
General Purpose EC2<br></br>
Memory Optimized EC2<br></br>
Storage Optimized EC2<br></br>
Compute Optimized EC2<br></br>
Accelerated EC2<br></br>

Let suppose when you go to IBM and ask them to give you a server. They ask you what type of servers you want? Then based on your usage/your application you answer them..Like if you want big data analytics then go for memory optimized server or if you want fast computations for bitcoin etc then go for a  memory optimized EC2.<br></br>

In interview usually interviewer asked kay what type of EC2 instances you prefer or you use? The answer is: based on my application complexity or usage it varies.<br></br>

In the same way we ask aws to give us a general purpose ec2 instance for this demo. Steps to create all types of ec2 instances are exactly same only price varies. <br></br>


# Availablility Zones and Regions:<br></br>
Aws have services across the world so it is divided into multiple regions like Asia, Eurpoe, USA and in each region it have multiple Availablity zones. Incase of any issue at one availability zone the other availabilityzone is responsible to provide the services efficiently. And the selection of regions depends on multiple reasons like if you are in Europe and want less latency then you would select the region of your instance in Europe instead of Asia etc.<br></br>
Let suppose you are working for a bank in Europe and the rule is to not put data outside of Europe for security purposes so in this case you should use the region in Europe not in Asia or any other.<br></br>

# Inbound and Outbound Traffic Request:<br></br>
Inbound traffic is the request that is coming inside aws to your EC2 instance and outbound is the request that goes outside. <br></br>

# DAY 4 VPC (Virtual Private Cloud):<br></br>
Let’s understand this concept with a very easy example.<br></br>
Let suppose there’s a village and some lazy persons are present in this village. These persons are so much lazy enough kay they are unable to make their houses because house making process takes time, effort etc. There is also one wise person living in this village. The wise person takes their laziness as an advantage. The wise person purchased a big land in the village and asked the lazy person that you are lazy enough to build the houses but you want the house to live so no problem just tell me your house requirement I will build the house for you in my purchased area according to your requirement and you have to pay me for this. The lazy people agreed on the deal and they paid the wise man and in return they got their houses. But another group of people living in the village noticed one thing they said there’s a privacy breach. In order to save the money, what wise man did? He make the houses very close to each other and any person can easily be accessible by any house and if privacy of one house breach then privacy of other houses may ultimately breach which raised the security concerns. We don’t want this type of houses. Infact we want the houses that are more secure. After this what wise man did? In order to save his business.. He proposed another plan. He said ok, If you people come in a group then, I create a secure property in my purchased area and I create houses in that secured area. Now only authorized persons (like you, your relatives and the persons you know) be only able to come to your house. For this purpose, I create a main gate at the front of the secure property so anyone who want to come to secure property he first authorized to the main gate. After entering through the main gate there are houses of multiple people and visitor wants to go to a Mr. A home then what happened inside the secure property there’s a guider that guide the visitor to Mr. A home. After reaching the Mr. A home the visitor is again checked for authorization. If visitor is authorized then he is able to enter in Mr. A home. <br></br>
This approach is liked by everyone and other people in the village is fascinated by this plan and they ask the wise man to make a security group for their tribe as well. In this way wise man create a multiple secure property in his purchased area.(For more clarity see picture which is present in document)<br></br>
 
# Now in Terms of DevOps Perspective:<br></br>
Like the same way wise man purchased a big land in the same way AWS have a big region across the world like in Ohio or in Mumbai. <br></br>
Let suppose there are 3 companies named company1, company2, company3 and one startup named startup1. These companies are fed up with managing their datacenters and startup don’t have enough money to build its own datacenter so what happened AWS said to these companies and startup kay no need to worry you can host your application in my data centers. I have datacenters across the world just say in which region you want to host your application and I host your application in that region or request the EC2 instances/VMs. I will give you as many VMs as you want. How AWS host? We assume company1 wants 2 VM, company 2 wants 3 VM, company 3 wants 1 VM and startup wants 1 VM. What aws do? AWS host all these VMs on one single server. As startup have less money so they don’t spend much on security. So, what happened? After some time a hacker be able to hack the startup VM and now he is able to hack VMs of other companies as well because they are also present in the same server. So, inshort by hacking one VM hacker is able to hack the entire server. This is a big issue. So after 2014, a concept of Virtual Private Cloud comes in where companies or group of companies can create their own VPC and this VPC is configured by devops engineer by reading the aws provided documentation and according to company need.<br></br>
Now let’s take an example for only one organization let say TCS and there’s one project under DevOps in this organization. Now we ask aws to create a VPC for this organization. Aws ask for size of the VPC? In previous scenario we set the size of land in terms of hecter and acre but in aws VPC we set the size by setting the IP address range. Let suppose I say IP address range for my VPC is 172.20.0.0/16 it means 255*255=65025 ip address are assigned for the instances in this VPC. TCS is one project there are many small/sub projects in it as well(like one project related to payment, other related to transaction etc) so in VPC for internal projects devops engineer will split the ip among those internal projects like 172.20.10.0/16 (means 255 ip addresses) given to payment related project, 172.20.11.0/16 (means 255 ip addresses) given to transaction related project and these are called subnet mask (private subnets bcz they don’t have access to internet). Now after this we want to make our app accessible to the customer and as we said earlier we setup a main entry gate through which only authorize one can go this entry gate. This gate way is actually a pass to entry in the VPC. This gateway is called internet gateway. After this entrance, we are present on Public Subnet and loadbalancer is associated with this publicsubnet. Loadbalancer don’t know where to go. Loadbalancer knows the target group but don’t know the route (usey pta hota ha kay usney kidhr jana ha but rasta nhi pta hota usey).So, route table can help to reach the destination but at destination let suppose there is a security guard here which we can say is security group that ask ok on which port do you want to access me or from which IP address you are coming from? What is your ip address then security group said ok only if your are coming from particular ip address through the internet then I will allow you the access and that way you will finally reach to your application.<br></br>
In simple terms jb ap bahria jatey ho main gate pay gurad hota ha ap us say clearance karwatey ho kay meray relaitives ka ghr ha idher phir ap apna id card submit karwatey ho aur ander jatey ho..phir enter honey kay baad ap roads, fountains, statues dekhtey ho ye public subnet ha aur logo kay ghr private subnet hain jo abhi nazer nhi a rhy ander thora sa jao ga street may tb nazer ayein gay..ab mainey let suppose Mr.Ali kay ghr jana ha..mujhe ye tou pta ha kay jana ha but rasta nhi pta ma aik loadbalancer hu… tou ma signs board ko dekh kay jao ga aur signboards ko hum routetable boltey hain. Phir ma Mr. Ali kay ghr chala gya ab us kay ghr kay bahir bhi aik guard khara ha (NAT) ab ye guard meray say pochey ga kay btao kidher say ao ho> kis say milna ha? Ma phir is guard ko saari detail du ga us kay baad hi ma Mr.Ali kay ghr may enter ho saku ga. (For more clarity see picture which is present in document)<br></br>
 
# NACL:<br></br>
Let suppose I want to attach the same security group (guards infront of houses) to multiple EC2 instances within a same subnet or want to repeat the security group configuration so instead of doing this all the time instead we use NACL they are basically automation for the security groups. Instead of defining each and every method again and again we can define as part of NACL.<br></br>

# NAT Gateways:<br></br>
Let suppose your EC2 inside VPC wants to download something from internet but due to security reasons you don’t want to expose the VPC EC2 IP to outside world but downloading is necessary so what we can do? We use the NAT gateway… NAT adds a mask to the IP (or we can say it changes the IP) and access the thing outside the VPC. NAT will try to mask the IP address It will change the IP address with the public IP address either of the load balance or either of the router. If it is using loadbalancer we say SNAT and if it is using route table we say it NAT gateway. <br></br>


# GPT PERSPECTIVE:<br></br>
# What is a VPC?<br></br>
A VPC is like your own private neighborhood in the cloud.<br></br>
•	Just like a real neighborhood, you can control who can enter, where the roads go, and how the houses (servers) are built.<br></br>
•	In AWS, a VPC is your isolated network where you can launch AWS resources like EC2 servers, databases, and load balancers safely.<br></br>
________________________________________<br></br>
# Key Components of a VPC with Real-Life Examples<br></br>
1.	Subnets – like blocks in your neighborhood<br></br>
o	You can divide your VPC into smaller sections called subnets.<br></br>
o	Example:<br></br>
	A public subnet = the houses facing the main road (accessible to everyone).<br></br>
	A private subnet = the houses inside, away from the main road (only you and your guests can access).<br></br>
2.	Internet Gateway (IGW) – like the main gate of the neighborhood<br></br>
o	If you want your neighborhood to connect to the city (internet), you install a main gate.<br></br>
o	Example: EC2 servers in public subnets can use this gate to access the internet.<br></br>
3.	NAT Gateway – like a private driveway with security<br></br>
o	Your inner houses (private subnets) can’t go directly to the city (internet) but can go through a secure driveway (NAT).<br></br>
o	Example: Your private database server downloads updates via NAT but isn’t directly exposed to the internet.<br></br>
4.	Route Tables – like street signs in your neighborhood<br></br>
o	They decide where traffic goes inside your VPC and to the outside world.<br></br>
o	Example: A street sign tells public subnet traffic to go to the Internet Gateway, while private subnet traffic goes to the NAT Gateway.<br></br>
5.	Security Groups & Network ACLs – like fences and security guards<br></br>
o	They control who can enter or leave each house.<br></br>
o	Example: Only your office computers can access your database server, like a locked gate.<br></br>
________________________________________<br></br>
# Real-Life Analogy: Building Your Cloud Office<br></br>
Imagine you’re building an office campus:<br></br>
•	VPC = the whole campus<br></br>
•	Subnets = different areas (office buildings, storage, parking)<br></br>
•	Internet Gateway = main entrance for visitors<br></br>
•	NAT Gateway = service entrance for deliveries<br></br>
•	Route Tables = signs showing directions<br></br>
•	Security Groups = office locks, keycards for employees<br></br>
With all this, you control who can go where, which buildings connect to the outside world, and how traffic flows safely.<br></br>

# EXTRA THINGS:

# SSH
SSH stands for Secure Shell.<br></br>
It’s a secure way to connect to another computer over a network, usually to control a server remotely.<br></br>
In simple terms<br></br>
SSH lets you:<br></br>
•	Log in to another computer from far away<br></br>
•	Run commands as if you were sitting in front of it<br></br>
•	Do all of this safely (encrypted)<br></br>
Why SSH is important<br></br>
•	🔐 Encrypted: Passwords and data can’t be easily stolen<br></br>
•	🌍 Remote access: Manage servers from anywhere<br></br>
•	⚙️ Admin tasks: Install software, edit files, restart services<br></br>
# Common uses<br></br>
•	Connecting to a Linux server<br></br>
•	Managing cloud servers (AWS, Azure, etc.)<br></br>
•	Secure file transfer (using scp or sftp)<br></br>
•	Git connections (e.g., GitHub via SSH keys)<br></br>

# Basic example<br></br>
ssh username@server_ip<br></br>
# Example:<br></br>
ssh alice@192.168.1.10<br></br>
SSH keys (very common)<br></br>
Instead of passwords, SSH often uses key pairs:<br></br>
•	🔑 Private key → stays on your computer<br></br>
•	🔓 Public key → stored on the server<br></br>
This is more secure than passwords.<br></br>

# SUBNET AND SUBNET MASK: (More understanding needed on this topic, watch video from youtube)<br></br>

# 🌐 First: What is an IP address? (VERY important)<br></br>
Every device on a network has an IP address.<br></br>
Think of it like a home address.<br></br>
Example IP:<br></br>
192.168.1.10<br></br>
This number tells:<br></br>
•	Which network the device is in<br></br>
•	Which device it is inside that network<br></br>
________________________________________<br></br>
# 🏘️ What is a Network?<br></br>
A network is a group of devices that can talk to each other.<br></br>
Example:<br></br>
•	All devices connected to your Wi-Fi router<br></br>
•	All computers inside an office<br></br>
________________________________________<br></br>
# 🧩 Now… What is a Subnet?<br></br>
Simple definition:<br></br>
A subnet is a smaller network inside a bigger network.<br></br>
________________________________________<br></br>
# 🏙️ Real-life example (BEST way to understand)<br></br>
Imagine:<br></br>
•	A city = Big network<br></br>
•	Areas / blocks inside the city = Subnets<br></br>
•	Houses = Devices<br></br>
Instead of one giant messy city, we divide it into organized areas.<br></br>
________________________________________<br></br>
# Why do we create subnets?<br></br>
1.	🚀 Faster communication<br></br>
2.	🔐 Better security<br></br>
3.	🧠 Easier management<br></br>
4.	📉 Less network traffic<br></br>
So:<br></br>
Subnet = splitting one big network into smaller parts<br></br>
________________________________________<br></br>
# 🎭 What is a Subnet Mask?<br></br>
Now comes the key part.<br></br>
Simple definition:<br></br>
A subnet mask tells:<br></br>
“Which part of the IP address is the network, and which part is the device”<br></br>
________________________________________<br></br>
# 📦 IP Address has TWO parts<br></br>
Example:<br></br>
192.168.1.10<br></br>
•	192.168.1 → Network part<br></br>
•	10 → Device (host) part<br></br>
But how does the computer know this?<br></br>
👉 Using the subnet mask<br></br>
________________________________________<br></br>
# 🎭 Subnet Mask Example<br></br>
Common subnet mask:<br></br>
255.255.255.0<br></br>
Put them together:<br></br>
IP Address	192.168.1.10<br></br>
Subnet Mask	255.255.255.0<br></br>
This mask says:<br></br>
•	First 3 numbers = network<br></br>
•	Last number = device<br></br>
________________________________________<br></br>
# 🧠 Easy trick to remember<br></br>
•	255 = network part<br></br>
•	0 = device part<br></br>
So:<br></br>
255.255.255.0<br></br>
means:<br></br>
Network.Network.Network.Device<br></br>
________________________________________<br></br>
# 🏠 What devices belong to the same subnet?<br></br>
With:<br></br>
Network: 192.168.1.0<br></br>
Mask:    255.255.255.0<br></br>
Devices in SAME subnet:<br></br>
•	192.168.1.1<br></br>
•	192.168.1.5<br></br>
•	192.168.1.200<br></br>
Devices in DIFFERENT subnet:<br></br>
•	192.168.2.10 ❌<br></br>
•	10.0.0.5 ❌<br></br>
________________________________________<br></br>
#🚦 Why subnet mask is CRUCIAL<br></br>
Before sending data, your computer asks:<br></br>
“Is this device in my subnet?”<br></br>
•	✅ YES → send directly<br></br>
•	❌ NO → send to router<br></br>
Subnet mask helps answer this question.<br></br>
________________________________________<br></br>
# 🧮 CIDR notation (small but important)<br></br>
Sometimes you’ll see:<br></br>
192.168.1.0/24<br></br>
This means:<br></br>
•	/24 → first 24 bits are network<br></br>
•	Same as:<br></br>
255.255.255.0<br></br>
Common ones:<br></br>
CIDR	Subnet Mask<br></br>
/8	255.0.0.0<br></br>
/16	255.255.0.0<br></br>
/24	255.255.255.0<br></br>
________________________________________<br></br>
# 🔪 Subnetting (splitting networks)<br></br>
Example:<br></br>
•	One network: 192.168.1.0/24<br></br>
•	254 devices possible<br></br>
Split into 2 subnets:<br></br>
•	192.168.1.0/25<br></br>
•	192.168.1.128/25<br></br>
Each subnet:<br></br>
•	126 devices<br></br>
This is subnetting.<br></br>
________________________________________<br></br>
# 🛑 Special addresses in a subnet<br></br>
For 192.168.1.0/24:<br></br>
Address	Meaning<br></br>
192.168.1.0	Network address<br></br>
192.168.1.1	First device<br></br>
192.168.1.254	Last device<br></br>
192.168.1.255	Broadcast<br></br>
You cannot assign:<br></br>
•	Network address<br></br>
•	Broadcast address<br></br>
________________________________________<br></br>
# 🧠 One-line summary<br></br>
•	Subnet = small network inside a big one<br></br>
•	Subnet mask = tells which part is network & which part is device<br></br>
•	Purpose = speed, security, organization<br></br>
________________________________________<br></br>
# 🔚 Final analogy (easy to remember)<br></br>
📍 IP address → House number<br></br>
🏘️ Subnet → Area / block<br></br>
🎭 Subnet mask → Map showing area boundaries<br></br>
🚦 Router → Post office between areas<br></br>
# DAY 5 (Security Groups and NACL):
VPC introduces the concept of Virtual Private Cloud in the world of Public Cloud. After the VPC mechanism like internet gateway (Main checkpost before entering in RWP) say pass hogya loadbalancer nay request agey forward kr di phir let suppose E block may gya aur udher E block may aik aur guard ha (society main gate guard) jis say pass kr kay logo kay ghr may jye ga (guard outside home). Once the load balancer forwards the request to the private subnet If we add more security at a subnet level. What we will do? We will start using NACLs (main building gate guard) and even if we bypass this we can add security at EC2 level (the location where our application is actually deployed) so at the EC2 level if we add more security we call it security group.<br></br>
In aws, there are multiple layers where we add security because security is a very important component. Any organization that moves to public cloud it first see’s the security of that public cloud regardless of cost and anything else because all important info of the organization is present on the public cloud.<br></br>


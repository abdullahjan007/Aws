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
Now let’s take an example for only one organization let say TCS and there’s one project under DevOps in this organization. Now we ask aws to create a VPC for this organization. Aws ask for size of the VPC? In previous scenario we set the size of land in terms of hecter and acre but in aws VPC we set the size by setting the IP address range. Let suppose I say IP address range for my VPC is 172.20.0.0/16 it means 255*255=65025 ip address are assigned for the instances in this VPC. TCS is one project there are many small/sub projects in it as well(like one project related to payment, other related to transaction etc) (In the same way Bahria is one housing society and there are multiple blocks in this society) so in VPC for internal projects devops engineer will split the ip among those internal projects like 172.20.10.0/16 (means 255 ip addresses) given to payment related project, 172.20.11.0/16 (means 255 ip addresses) given to transaction related project and these are called subnet mask (private subnets bcz they don’t have access to internet). Now after this we want to make our app accessible to the customer and as we said earlier we setup a main entry gate through which only authorize one can go this entry gate. This gate way is actually a pass to entry in the VPC. This gateway is called internet gateway. After this entrance, we are present on Public Subnet and loadbalancer is associated with this publicsubnet. Loadbalancer don’t know where to go. Loadbalancer knows the target group but don’t know the route (usey pta hota ha kay usney kidhr jana ha but rasta nhi pta hota usey).So, route table can help to reach the destination but at destination let suppose there is a security guard here which we can say is security group that ask ok on which port do you want to access me or from which IP address you are coming from? What is your ip address then security group said ok only if your are coming from particular ip address through the internet then I will allow you the access and that way you will finally reach to your application.<br></br>
In simple terms jb ap bahria jatey ho main gate pay gurad hota ha ap us say clearance karwatey ho kay meray relaitives ka ghr ha idher phir ap apna id card submit karwatey ho aur ander jatey ho..phir enter honey kay baad ap roads, fountains, statues dekhtey ho ye public subnet ha aur logo kay ghr private subnet hain jo abhi nazer nhi a rhy ander thora sa jao ga street may tb nazer ayein gay..ab mainey let suppose Mr.Ali kay ghr jana ha..mujhe ye tou pta ha kay jana ha but rasta nhi pta ma aik loadbalancer hu… tou ma signs board ko dekh kay jao ga aur signboards ko hum routetable boltey hain. Phir ma Mr. Ali kay ghr chala gya ab us kay ghr kay bahir bhi aik guard khara ha (NAT) ab ye guard meray say pochey ga kay btao kidher say ao ho> kis say milna ha? Ma phir is guard ko saari detail du ga us kay baad hi ma Mr.Ali kay ghr may enter ho saku ga. (For more clarity see picture which is present in document)<br></br>
 
# NACL:<br></br>
Let suppose I want to attach the same security group (guards infront of houses) to multiple EC2 instances within a same subnet or want to repeat the security group configuration so instead of doing this all the time instead we use NACL they are basically automation for the security groups. Instead of defining each and every method again and again we can define as part of NACL.<br></br>

# NAT Gateways:<br></br>
Let suppose your EC2 inside VPC wants to download something from internet but due to security reasons you don’t want to expose the VPC EC2 IP to outside world but downloading is necessary so what we can do? We use the NAT gateway… NAT adds a mask to the IP (or we can say it changes the IP) and access the thing outside the VPC. NAT will try to mask the IP address It will change the IP address with the public IP address either of the load balance or either of the router. If it is using loadbalancer we say SNAT and if it is using route table we say it NAT gateway. <br></br>
For private subnet we use NAT for internet access of our app/instance<br></br>


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
# Something about loadbalancer (Side Topic/Side Thing): <br></br>
Loadbalancer is usually placed by devops engineers in public subnet. It can be directly access to the outside world and this load balancer can also forwards the request to the private subnet or it can have access to the private subnet.<br></br>
<br></br>
VPC introduces the concept of Virtual Private Cloud in the world of Public Cloud. After the VPC mechanism like internet gateway (Main checkpost before entering in RWP) say pass hogya loadbalancer nay request agey forward kr di phir let suppose E block may gya aur udher E block may aik aur guard ha (society main gate guard) jis say pass kr kay logo kay ghr may jye ga (guard outside home). Once the load balancer forwards the request to the private subnet If we add more security at a subnet level. What we will do? We will start using NACLs (main building gate guard) and even if we bypass this we can add security at EC2 level (the location where our application is actually deployed) so at the EC2 level if we add more security we call it security group.<br></br>
In aws, there are multiple layers where we add security because security is a very important component. Any organization that moves to public cloud it first see’s the security of that public cloud regardless of cost and anything else because all important info of the organization is present on the public cloud.<br></br>

AWS said security is a shared responsibility. What this mean? AWS said, we can add as much security as possible from our side like NACL, SG etc but as it is a shared responsibility so we did our part and we need devops Engineers or network admin or AWS admin to do their part of security as well. <br></br>
SG and NACL is the last part of security in AWS and it is very critical because if we left this last part of security unattended there might be a chance kay our application got hacked.<br></br>

# Security Groups:<br></br>
Now discuss about Security Groups. Security Groups are at instance level. When we create an AWS account, aws gives us a bydefault VPC. AWS don’t do anything or any work without VPC so that’s why it create bydefault VPC but we can create our custom VPC as well. In Day 3, we create an EC2 instance and deployed the Jenkins on it but we are unable to access the Jenkins app because something is blocking it so what we can do we configure the security groups at instance level. We allowed the port 8080 and also allowed all the traffic after this we are able to access the Jenkins app. As, we dicussed earlier, AWS said security is a shared responsibility. So aws done its part by not allowing the traffic and now as a devops engineer its’s your responsibility to configure the security according to your need. Like in this case we configure the security by allowing all traffic and port 8080 but keep in mind don’t allow multiple ports randomly because it cause unnecessary traffic to reach your application or EC2 instance and also let suppose you open the port 9000 and that port is not in use and some hacker might try to access this port which cause your app to be hacked as well.  <br></br>

Now there are two things in Security groups. One is inbound traffic and other is the outbound traffic. Inbound means anything coming to your application that is present in EC2 instance and outbound traffic means anytraffic that is going out of your application. Letsuppose you are using amazon.com so a user request something to amazon that is inbound traffic and based on your request lets assume amazon.com sends the request to google pay that’s the outbound traffic. Bydefault aws set security on both inbound and outbound. For outbound aws allows all the traffic except for port 25 but for inbound aws blocks the traffic. You have to set the inbound rules by going into Securty groups.<br></br>
AWS bedefault block the outbound traffic on port 25. The reason is port 25 is mailing service and aws don’t want any type of spamming activity and don’t want to locate or record the IP address of your application that is present in the EC2 instance.
If security groups are doing all the things then why there’s a need of NACL?<br></br>

# NACL(Network Access Control List):<br></br>
Public subnet ko hum kisi society kay blocks bhi samjh saktey hain..like block A of bahria, block B of bharia etc..<br></br>

NACL does NOT override Security Groups.<br></br>
Traffic must be allowed by BOTH.<br></br>
If NACL blocks, traffic is blocked even if SG allows.<br></br>

NACL is at subnet level. DevOps Engineers plays an important role at NACL level as well. Now take an example: Let suppose 1 EC2 instance is given to 1 development team and this development team deploys a Jenkins app or any other application on that instance and development teams know that they should not allow all the traffic on the instance they only allow certain traffic on certain ports like in case of Jenkins app only allow the traffic on 8080 port but to make the process easy and faster what the development team did? They simply allow all the traffic on their EC2 instance they ignore the aws security they don’t bother to set the inbound and outbound rules but as a devops engineer, network administrator, or administrator what you did? You set a rule or security at subnet level.. Let suppose you set a security at subnet level kay only traffic from Pakistan is allowed to reach the app that is deployed on the instance at port 8080 in a private subnet. So, what happened although at instance level (where we specify security group) you set the rule of allow all the traffic on all ports but at subnet level (where we specify the NACL) devops engineer also define some security rules… and client who wants to reach your app that is present in EC2 instance is first checked at NACL level if NACL security is passed then it is allowed to checked by security groups at instance level and if it is passed at security group as well then your client reach the application at EC2 instance level but in case your client fails to pass the security at NACL level then no matter it passed the security at seccurity group or not.. NACL just don't allow the client to enter and reach the app. (not cnfrm)<br></br>
# Confirm thing is as follow, in easy wording:<br></br>
NACL does NOT override Security Groups.<br></br>
Traffic must be allowed by BOTH.<br></br>
If NACL blocks, traffic is blocked even if SG allows. Means ager society ka guard hi ander nhi aney de rha tou E block tk ponch hi nhi sako gay<br></br>

In NACL you can set both inbound and outbound rules but in SG you allow only inbound rules, outbound rules are automatically allowed. <br></br>
NACL is also used for automation like if I set NACL for some private subnet (E block in a society tou ab E block may jitney bhi ghr ho gay saab pay ye rule apply ho ga) and in that subnet let suppose there are 1000 instances so same rule is applied to all 1000 instances you only have to set at NACL level.Scene aisa ha kay let suppose ap nay 1000 instances ya app pay koi rule define karna ha so instead of set all this on 1000 apps/instances bari bari what you can do you? put them in a private subnet and set a rule at NACL level is say hoga ye kay aik dafa rule set karney say all 1000 instances/apps pay same rule apply ho jye ga (not cnfrm) <br></br>
If we want to deny or block the traffic like what type of traffic we want to allow or what type of traffic we want to deny in that scenario we set the rule at NACL level.<br></br>
But Security group is only used for allowing traffic. Security group doesnot deny any trafiic<br></br>


# GPT Overview:<br></br>
# Big Picture (1-line summary)<br></br>
Security Groups = bodyguards at your house door<br></br>
NACLs = security gates at the society entrance<br></br>
Both control traffic, but at different levels.<br></br>
________________________________________<br></br>
# 1️⃣ Security Groups (SG)<br></br>
# 🏠 Real-life example<br></br>
Imagine your house:<br></br>
•	You have a door<br></br>
•	You decide who can enter<br></br>
•	If someone is allowed in, they can also leave freely<br></br>
➡️ That door is a Security Group<br></br>
________________________________________<br></br>
# 🧠 Easy definition<br></br>
A Security Group is a virtual firewall attached to a server (EC2 instance) that controls:<br></br>
•	Who can come in (inbound rules)<br></br>
•	Who can go out (outbound rules)<br></br>
________________________________________<br></br>
# 🔑 Key characteristics (easy words)<br></br>
Feature	Meaning<br></br>
Instance-level	Works on EC2 directly<br></br>
Stateful	If traffic is allowed in, response is automatically allowed out<br></br>
Allow rules only	❌ No “deny” rules<br></br>
Default deny	Everything blocked unless you allow it<br></br>
________________________________________<br></br>
# 🧑💻 Technical example<br></br>
You have a web server (EC2):<br></br>
Inbound rules:<br></br>
•	Allow HTTP (80) from 0.0.0.0/0<br></br>
•	Allow SSH (22) only from your IP<br></br>
Outbound rules:<br></br>
•	Allow all traffic<br></br>
# 👉 Result:<br></br>
•	Users can open the website<br></br>
•	Only you can SSH<br></br>
•	Server responses are automatically allowed<br></br>
________________________________________<br></br>
# 📌 When to use Security Groups?<br></br>
•	Protect individual EC2 instances<br></br>
•	Control application-level access<br></br>
•	Fine-grained security<br></br>
________________________________________<br></br>
# 2️⃣ NACL (Network Access Control List)<br></br>
# 🏢 Real-life example<br></br>
Imagine a gated society:<br></br>
•	Security guard checks everyone entering<br></br>
•	Security guard also checks everyone leaving<br></br>
•	Some people are explicitly blocked<br></br>
➡️ That gate is a NACL<br></br>
________________________________________<br></br>
# 🧠 Easy definition<br></br>
A NACL is a firewall that works at the network (subnet) level and controls:<br></br>
•	Inbound traffic<br></br>
•	Outbound traffic<br></br>
________________________________________<br></br>
# 🔑 Key characteristics (easy words)<br></br>
Feature	Meaning<br></br>
Subnet-level	Applies to all servers in subnet<br></br>
Stateless	Inbound & outbound must be allowed separately<br></br>
Allow & Deny rules	✅ Can explicitly block traffic<br></br>
Rule order matters	Lowest number wins<br></br>
________________________________________<br></br>
# 🧑💻 Technical example<br></br>
Subnet NACL rules:<br></br>
Inbound:<br></br>
•	Allow HTTP (80) from 0.0.0.0/0<br></br>
•	Deny SSH (22) from all<br></br>
Outbound:<br></br>
•	Allow HTTP responses (1024–65535)<br></br>
# 👉 Result:<br></br>
•	Website works<br></br>
•	SSH is blocked even if SG allows it<br></br>
________________________________________<br></br>
# 📌 When to use NACL?<br></br>
•	Extra layer of security<br></br>
•	Block specific IP ranges<br></br>
•	Control whole subnet traffic<br></br>
________________________________________<br></br>
#🔥 Security Group vs NACL (Simple Comparison)<br></br>
Feature	Security Group	NACL<br></br>
Level	EC2 instance	Subnet<br></br>
Stateful	✅ Yes	❌ No<br></br>
Allow/Deny	Allow only	Allow & Deny<br></br>
Rule order	Not important	Important<br></br>
Default	Deny all inbound	Allow all<br></br>
________________________________________<br></br>
# 🧠 Best Way to Remember<br></br>
•	Security Group = Who can knock on your door<br></br>
•	NACL = Who can enter your neighborhood<br></br>
# 💡 AWS best practice:<br></br>
Use both together → NACL for coarse control, SG for fine control<br></br>
How NACL and Security groups relate to each other?<br></br>

# Big Picture Relationship (1 line)<br></br>
Traffic must pass NACL first, then Security Group<br></br>
If either one blocks, traffic is blocked<br></br>
________________________________________<br></br>
# Step-by-step relationship (Real-life analogy)<br></br>
# 🏘️ Real life<br></br>
You visit a friend who lives in a society:<br></br>
1.	Society gate security checks you → NACL<br></br>
2.	Friend’s house door checks you → Security Group<br></br>
✔️ You enter only if both allow you<br></br>
________________________________________<br></br>
# Technical traffic flow (AWS)<br></br>
Incoming traffic path:<br></br>
Internet<br></br>
   ↓<br></br>
NACL (Subnet level)<br></br>
   ↓<br></br>
Security Group (EC2 level)<br></br>
   ↓<br></br>
EC2 Instance<br></br>
Outgoing traffic path:<br></br>
EC2 Instance<br></br>
   ↓<br></br>
Security Group<br></br>
   ↓<br></br>
NACL<br></br>
   ↓<br></br>
Internet<br></br>
________________________________________<br></br>
# How they depend on each other<br></br>
🔹 Rule #1: Both must allow traffic<br></br>
•	If NACL allows but SG blocks → ❌ Blocked<br></br>
•	If SG allows but NACL blocks → ❌ Blocked<br></br>
•	If both allow → ✅ Allowed<br></br>
________________________________________<br></br>
🔹 Rule #2: Stateful vs Stateless matters<br></br>
Scenario	What happens<br></br>
SG allows inbound	Response is automatically allowed<br></br>
NACL allows inbound	❗ Outbound must also be allowed<br></br>
👉 This is why NACL needs more rules<br></br>
________________________________________<br></br>
# Example (Very common exam & real case)<br></br>
Case: Web server (Port 80)<br></br>
NACL<br></br>
•	Inbound: Allow 80<br></br>
•	Outbound: Allow 1024–65535<br></br>
Security Group<br></br>
•	Inbound: Allow 80<br></br>
•	Outbound: Allow all<br></br>
✔️ Website works<br></br>
________________________________________<br></br>
# ❌ What if outbound NACL rule is missing?<br></br>
•	Request reaches server<br></br>
•	Response is blocked at NACL outbound<br></br>
•	Website does NOT load<br></br>
________________________________________<br></br>
# Who does what? (Clear responsibility split)<br></br>
# NACL	Security Group<br></br>
Broad network rules	Fine-grained instance rules<br></br>
IP blocking	Application access<br></br>
Subnet protection	Server protection<br></br>
First line of defense	Second line of defense<br></br>
________________________________________<br></br>
# Best Practice (Important)<br></br>
NACL = simple, strict, minimal rules<br></br>
Security Groups = detailed, application-specific rules<br></br>
Example:<br></br>
•	NACL: Allow HTTP, HTTPS, SSH only<br></br>
•	SG: Allow HTTP from all, SSH only from admin IP<br></br>
________________________________________<br></br>
# Interview one-liner (very useful)<br></br>
NACL acts as a subnet firewall and Security Group acts as an instance firewall; traffic must be allowed by both to reach the instance.<br></br>
I learned at one point kay something blocked at NACL level but allowed at SG level then the configuration that is done at NACL level is followed instead of SG level.. Let suppose if some developer by mistake allow all the traffic on all ports at SG level but i as a devops engineer set the rule at NACL level that only traffic with specific IP can reach at port 8080 so in that scenario NACL level policy is used...What are your thoughts on this?<br></br>
Short, correct statement (fixing the wording)<br></br>
NACL does NOT override Security Groups.<br></br>
Traffic must be allowed by BOTH.<br></br>
If NACL blocks, traffic is blocked even if SG allows.<br></br>
So in practice, NACL becomes the effective gate when it is more restrictive.<br></br>
________________________________________<br></br>
# Apply this to your scenario (step-by-step)<br></br>
Your setup (restated clearly)<br></br>
Security Group (mistake by developer):<br></br>
•	Inbound: Allow ALL traffic, ALL ports, ALL IPs<br></br>
NACL (your DevOps control):<br></br>
•	Inbound:<br></br>
o	Allow port 8080 from specific IP<br></br>
o	Deny everything else (explicit or implicit)<br></br>
________________________________________<br></br>
# What actually happens in AWS<br></br>
Incoming traffic flow:<br></br>
Client → NACL → Security Group → EC2<br></br>
Case 1:<br></br>
📌 Client from allowed IP, port 8080<br></br>
•	NACL: ✅ Allowed<br></br>
•	SG: ✅ Allowed (everything open)<br></br>
✔️ Traffic reaches EC2<br></br>
________________________________________<br></br>
Case 2:<br></br>
📌 Client from any other IP or any other port<br></br>
•	NACL: ❌ Blocked<br></br>
•	SG: ❓ Doesn’t matter (never reached)<br></br>
❌ Traffic is dropped at NACL<br></br>
________________________________________<br></br>
# Conclusion for your scenario<br></br>
✅ Your NACL rules are effectively enforced<br></br>
✅ You successfully protected the system<br></br>
❌ SG misconfiguration still exists but is neutralized<br></br>
So yes:<br></br>
Even if SG is wide open, NACL can stop traffic earlier<br></br>
________________________________________<br></br>
# Why this is NOT called “override”<br></br>
This is the subtle but important point 👇<br></br>
•	SG does not even get evaluated if NACL blocks<br></br>
•	SG and NACL are AND conditions, not priority-based<br></br>
Logical view:<br></br>
Traffic Allowed = NACL_ALLOW AND SG_ALLOW<br></br>
________________________________________<br></br>
# Why AWS designed it this way (security layering)<br></br>
This is called Defense in Depth:<br></br>
Layer	Purpose<br></br>
NACL	Coarse, admin-controlled guardrail<br></br>
SG	App-level, developer-controlled<br></br>
This is exactly why DevOps/SRE teams lock down NACLs:<br></br>
•	To protect against human mistakes<br></br>
•	To enforce organization-level boundaries<br></br>
________________________________________<br></br>
# Important caution (real production warning ⚠️)<br></br>
Using NACLs as primary security can cause issues:<br></br>
•	Stateless → easy to break apps<br></br>
•	More rules to maintain<br></br>
•	Harder to debug than SGs<br></br>
Best practice used by senior DevOps teams:<br></br>
•	NACL: minimal, restrictive, stable<br></br> wohi scene ha jb concert pay kisi uni ja rhy ho guard bs student card dekh kay allow kr de ga simple and stable (NACL bhi isi tarha ha stable and simple) but jb ap enter ho jye gay aur concert ground may enter honey say pehle ap ki detail checking hogi (Security group bhi isi tarha ha detailed and app-specific) 
•	SG: detailed, flexible, app-specific<br></br>
________________________________________<br></br>
# Interview-grade explanation (very strong answer)<br></br>
“NACLs don’t override Security Groups, but because traffic must pass both, a restrictive NACL effectively enforces security even if a Security Group is misconfigured. This allows DevOps teams to use NACLs as guardrails while Security Groups handle application-level access.”<br></br>
________________________________________<br></br>
# Final verdict on your thought process<br></br>
✅ Your intuition is right<br></br>
✅ Your example is valid<br></br>
🔧 Just replace the word “override” with “first line of enforcement”<br></br>

# DAY 6 (Route 53): (Aws uses port 53 for DNS that’s why its called route 53)
Route 53 in aws provides DNS as a service. Like the same way in EC2 aws provides compute as a service and in EKS aws provides kubernetes as a service. In the same way route 53 provides DNS as a service. DNS stands for Domain Name System. We are using DNS in our day to day daily life without knowing it. When we search for amazon.com or flipkart.com we actually use DNS.<br></br>
When we create a public and private subnet in a VPC , in private subnet we have our app and In public subnet we have load balancers. Our load balancer is getting the request and that request is then sends to our app in private subnet if load balancer is not present then request is directly send to the app.<br></br>
Whether it is application whether it is load balancer when we create these things on aws or on prem these things gets assigned with an ip address. But in real-life we don’t use the IP addresses we never access flipkart or amazon.com with server’s ip. So amazon.com and flipkart.com is actually the domain name on that server ip. Some one is responsible to convert the server ip into domain name and who did this? Answer is domain name service(DNS). So, inshort DNS service is the one that maps domain name with ip address. In real life scenario DNS resolves domain name to the load balancer IP address only. So, when you are accessing flipkart.com etc you are actually trying to resolve the load balancer IP address using the domain name.<br></br>
In VPC we have public and private subnet, in public subnet we have load balancers and in private subnet we have our app. First request goes to load balancer and then to our app that is present in private subnet. In real life scenario we usually use load balancer ip address but in real-life we don’t use ip address we actually use domain names due to 2 reasons: it is very difficult to remember the ip addresses like 10.20.25.1 for flipcart, 10.21.45.67 for amazon.com so we use the domain names like flipkart and amazon which is easy to remember and the second thing is kay ip address may be static or dynamic let suppose your ip address gets changes with the change of network so it is very difficult to remember the ip addresses that gets changed so every company uses domain name. 
DNS basically keeps a lot of records <br></br>
e.g: 10.20.22.1(serverip) aiabdullahproject.com(domain)<br></br>
Now what aws does? Aws provides DNS as a service. Now I might be thinking kay why I am doing that? I can setup my own dns but there are multiple things involved in this process like I make an application and I want my application to be accessible by the external world so what I can do? first I go to the godaddy and buy the domain abd.com if its not available then I search for another domain name like abd.org.com blaa blaa etc when I got the domain I need some hostimg solution like hostinger and then I have to maintained the dns all the time but in case of aws, aws said no problem don’t bother about all these things if you want to host your application on aws, on vpc  or somewhere else we will provide you with something called Route53<br></br>
Previously architecture aisa hota tha user amazon.com access karna chahta tha wo internet gateway kay through us ki req vpc may enter hoti ha aur agey loadbalancer us ko private subnet pay le kay jata ha but route53 kay aney say architecture thora sa change hua ha..ab scene ye ha kay internet gateway kay baad route53 ha aur phir loadbalancer ha ab hota aisa ha kay amazon.com ki request internet gateway say ho kay route53 pay jati ha.. route53 apney records may us ki dns dekhta ha aur then tries to resolve the DNS to the IP address of the load balancer and after this process is same as previously discussed.<br></br>
To configure Route53 we need to configure a lot of things.<br></br>
In aws there are few critical things for route53 that we need to configure first one is basically domain registration itself and the second is hosted zones.<br></br>
As a devops engineer you configure all the things and now you are about to live your application but the first thing that you need to do is buy a domain. AWS said no problem you can purchase/buy/register a domain from me as well but if you already purchased a domain from godaddy or from any other platforms then its still not a problem I can integrate this domain as well and for this you have to create a hosted zone and basically in this hosted zone all the DNS record of your app is present.<br></br>
So request goes to route53 after internet gateway and route53 check for DNS records in hosted zone if he found then he resolve the ip and forwards the request to the loadbalancer and so on.<br></br>
Route53 also supports healthcheck. Letsuppose there are 2 servers in same or different availability zones..Health check can check the health of webservers after ever 5-10 mins(the interval set by us) and if one webserver out of many is unhealthy then route53 don’t send the request to that webserver but if all are healthy then it sends the request to loadbalancer.<br></br>


# DAY 7 (Project):
We will create a project.. In this project we have a VPC and in that VPC we have a public subnet and private subnet.. in public subnet we have a nat gateway and loadbalancer and in private subnet we have a server..We use the two availability zones because if one availability zone gets destroy we still have our app running on second avalibility zone..The reason for using the NAT gateway is kay if our app wants to access some api from internet we mask the ip of server with the public ip of NAT because if some hacker might to hack the app he only gets the public ip of nat not the ip of app/server in private subnet. We use loadbalancer because request that is coming from internet is first going to loadbalancer and then loadbalancer further sends it to the app/server. The purpose of loadbalancer is kay if 100 requests are incoming then load balancer managing the load by sending 50 request to one server and other 50 requests to the other server or send the 80 requests to healthy server and 20 requests to unhealthy server. We also use autoscaling like in our case we use 2 availability zone so instead of creating 2 ec2 instances we use 2 replicas and if more and more requests are incoming then instances are increasing or decreasing automatically.(not cnfrm)<br></br>
# Bastion Host and Jump Server:
Our server/ec2 is in a private subnet so they don’t have a public IP and we cannot ssh into these instances directly and can’t create public ip address for it so what we can do?.. we can create a bastion host or jump host in public subnet and through that we can connect to our ec2 instance in private subnet. Flow is -> we first connect to bastion host and then from bastion host we connect to our ec2. With bastion we have a proper logging mechanism etc. <br></br>

# Q: What is Elastic IP address? <br></br>
Elastic ip address in aws is nothing but an ip address that will remain the same even if instance is deleted or terminated, we can also say it as a static ip address. Let’s take an example, if we assign an elastic ip to an ec2 instance then if the ec2 instance goes down and come back the ip still remains the same. <br></br>

# AutoScaling Group:<br></br>
Autoscaling group in aws can’t be created directly we can use the launch template. So why you need the launch template? Because we can use this launch template across multiple autoscaling groups or this template acts as a reference like tomorrow if I want to understand kay how my autoscaling group behaving.. is my autoscaling group scaling one instance, 10 instance, 100 instance so we can use this launch template as a reference.easy wording may samjho like mainey 3 templates bna liye aur template1 10 instances launch/scale karta ha, isi tarha template2 100 instances so on so forth tou ab ager mujhe 100 instance scaling chahiye tou ma us kay sath template2 link kr du ga (not cnfrm) <br></br>

# IMP:
ab humney apney local pc say bastion host ko connect karna ha aur phir humney bastian say private subnet ko connect karna ha..<br></br>
local say bastian tk connect karney kay liye key-value pair jo laptop download kia ha use kr lein ge with the help of this command ssh -i login_aws.pem ubuntu@<bastianhost-serverip> aur hum bastian host may chaley gye but bastian say private subnet ko connect karney kay liye bhi tou humey key-value pair chahiye na wo key value pair hum bastian host pay kaisey le kr jyein gay? Us kay liye hum scp (Secure copy command use karein ge us say hoga ye kay local pay jo key-value pair download the wo bastian host pay bhi copy ho jye ga)<br></br>
Command: scp -I User/Downloads/Abdullah login-aws.pem User/Downloads/Abdullah login-aws.pem ubunutu@<bastian-Server-pi>:home/ubuntu<br></br>
is command say hoga ye kay hum bastian host pay connect kr kay jb ls karein gay tou udher bhi ye pari hogi.<br></br>

# THE FOLLOWING LINE I COPIED FROM SOMEONE'S COMMENT ON DAY-07 VIDEO OF PLAYLIST AWS ZERO TO HERO <br></br>
We can login to private hosts from bastion host with out copying pem file to bastion host. If you copy pem file to bastion host it is security breach as if attacker  can access to bastion host since it has public ip and with pem file in bastion he can access to private hosts as well<br></br>

# DAY 8 (Interview Questions): <br></br>
# Q1: You have been assigned to design a VPC architecture of a 2-tier application. The application needs to be highy available and scalable. How would you design the VPC architecture? <br></br>

# My answer: <br></br>
For high scalibilty I use Auto Scaling group because  it automatically scales up and down the instances according to the need, and for high availability I use multi region availability zones because if my app goes down in one zone its still accessible from other zone. I also use load balancer so that it sends requests to multiple instances not only on one instance for durability.<br></br>
#  Abhishek Answer: <br></br>
In this scenario, I would design a VPC architecture in the following way.<br></br>
I would create 2 subnets; public and private. The public subnet would contain the load balancers and be accessible from the internet. The private subnet would hold the application servers.<br></br>
I would distribute the subnets across multiple AZ for high availability. Additionally, I would configure autoscaling group for the application servers.<br></br>
# Q2: Your organization has a VPC with multiple subnets. You want to restrict outbound internet access for resource in on subnet, but allow outbound internet access for resource in another subnet. How would you achieve this?<br></br>
# My answer:<br></br>
Let's assume in VPC i have 1 AZ and in that AZ i have two subnets and in each subnet there are instances and for each subnet i have separate SG and NACL and in SG we don't have to set the outbound traffic (because SG’s are stateful) rule bydefault but in NACL we are supposed to set the outbound traffic rule (because NACL are stateless). So i allow the all traffic rule in a subnet that need the allow outbound internet access and deny the traffice for the subnet that don't allow outbound internet access.<br></br>

# GPT perspective on my answer:
Short answer: your answer is partially correct, but it is not sufficient or recommended by itself.<br></br>
Why your NACL-based answer is not fully correct<br></br>
You suggested:<br></br>
•	Using separate subnets<br></br>
•	Allowing outbound traffic in NACL for one subnet<br></br>
•	Denying outbound traffic in NACL for the other subnet<br></br>
✅ What you got right<br></br>
•	NACLs are subnet-level → correct<br></br>
•	NACLs can allow/deny outbound traffic → correct<br></br>
•	Denying outbound rules will block traffic → correct<br></br>
So technically:<br></br>
Yes, denying outbound traffic in a NACL will stop internet access.<br></br>
________________________________________<br></br>
❌ Why this is not the correct architectural answer<br></br>
1️⃣ Internet access is determined by routing, not just firewalls<br></br>
For a resource to reach the internet, it needs:<br></br>
1.	A route to the internet (IGW or NAT)<br></br>
2.	Firewall rules that allow the traffic<br></br>
If a subnet has no route to the internet, traffic cannot leave, even if:<br></br>
•	Security Groups allow it<br></br>
•	NACLs allow it<br></br>
➡️ Route tables are the primary control mechanism<br></br>
________________________________________<br></br>
2️⃣ NACLs are stateless and coarse-grained<br></br>
Problems with using NACLs for this purpose:<br></br>
•	Stateless → return traffic must be explicitly allowed<br></br>
•	Hard to manage at scale<br></br>
•	Not designed to control connectivity architecture<br></br>
•	One mistake can break internal traffic as well<br></br>
AWS best practice:<br></br>
Use route tables to control reachability<br></br>
Use NACLs for additional security boundaries<br></br>
________________________________________<br></br>
3️⃣ Exam / interview expectation<br></br>
If this is:<br></br>
•	AWS exam<br></br>
•	Interview question<br></br>
•	Architecture design<br></br>
Then the expected answer is:<br></br>
Use separate route tables per subnet to control outbound internet access.<br></br>
Using only NACLs would be considered:<br></br>
•	❌ Incomplete<br></br>
•	❌ Not best practice<br></br>
•	❌ Not how AWS expects you to design VPC networking<br></br>

# 1️⃣ Stateful<br></br>
# Definition:<br></br>
A firewall or rule is stateful if it remembers the state of a connection.<br></br>
•	This means if an incoming request is allowed, the return traffic is automatically allowed — no need for explicit rules.<br></br>
# 🔹 AWS Example: Security Groups<br></br>
•	Security Groups are stateful.<br></br>
•	If you allow outbound traffic to the internet:<br></br>
o	The return inbound traffic is automatically allowed.<br></br>
•	If you allow inbound traffic from a subnet:<br></br>
o	The reply outbound traffic is automatically allowed.<br></br>
# Example:<br></br>
•	You allow outbound TCP port 80 (HTTP) from your instance to 0.0.0.0/0.<br></br>
•	When the web server responds back, you don’t need an inbound rule — the Security Group automatically allows the return traffic.<br></br>
✅ Key point: Stateful “remembers” the session.<br></br>
________________________________________<br></br>
# 2️⃣ Stateless<br></br>
# Definition:<br></br>
A firewall or rule is stateless if it does NOT remember the connection.<br></br>
•	You must explicitly allow both inbound and outbound traffic.<br></br>
🔹 AWS Example: Network ACLs<br></br>
•	Network ACLs are stateless.<br></br>
•	If you allow outbound traffic on port 80:<br></br>
o	You must also allow inbound return traffic (typically ephemeral ports 1024-65535) explicitly.<br></br>
•	Each packet is evaluated independently — no memory of previous packets.<br></br>
# Example:<br></br>
•	Outbound HTTP traffic allowed to 0.0.0.0/0 (port 80).<br></br>
•	Return traffic from the web server will be blocked unless there is an inbound rule allowing it.<br></br>
❌ Key point: Stateless “forgets” everything — you have to define rules both ways.<br></br>




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
Elastic ip address in aws is nothing but an ip address that will remain the same even if instance is deleted or terminated (not cnfrm), we can also say it as a static ip address. Let’s take an example, if we assign an elastic ip to an ec2 instance then if the ec2 instance goes down and come back the ip still remains the same. <br></br>
# 🌐 Public IP<br></br>
A public IP is an address given to a server so it can be reached from the internet.<br></br>
It is automatically assigned when you start a cloud server (like an EC2 instance).<br></br>
Problem:<br></br>
If you stop or restart the server, this IP can change.<br></br>
Think of it like a temporary phone number 📱.<br></br>
# 🔒 Elastic IP (EIP)<br></br>
An Elastic IP is a fixed (static) public IP provided by cloud services like AWS.<br></br>
It does not change, even if you stop or restart the server.<br></br>
You can move it from one server to another if something fails.<br></br>
Think of it like a permanent phone number ☎️.<br></br>

# AutoScaling Group:<br></br>
Autoscaling group in aws can’t be created directly we can use the launch template. So why you need the launch template? Because we can use this launch template across multiple autoscaling groups or this template acts as a reference like tomorrow if I want to understand kay how my autoscaling group behaving.. is my autoscaling group scaling one instance, 10 instance, 100 instance so we can use this launch template as a reference.easy wording may samjho like mainey 3 templates bna liye aur template1 10 instances launch/scale karta ha, isi tarha template2 100 instances so on so forth tou ab ager mujhe 100 instance scaling chahiye tou ma us kay sath template2 link kr du ga (not cnfrm) <br></br>

# IMP:
ab humney apney local pc say bastion host ko connect karna ha aur phir humney bastian say private subnet ko connect karna ha..<br></br>
local say bastian tk connect karney kay liye key-value pair jo laptop download kia ha use kr lein ge with the help of this command ssh -i login_aws.pem ubuntu@<bastianhost-serverip> aur hum bastian host may chaley gye but bastian say private subnet ko connect karney kay liye bhi tou humey key-value pair chahiye na wo key value pair hum bastian host pay kaisey le kr jyein gay? Us kay liye hum scp (Secure copy command use karein ge us say hoga ye kay local pay jo key-value pair download the wo bastian host pay bhi copy ho jye ga)<br></br>
Command: scp -I User/Downloads/Abdullah login-aws.pem User/Downloads/Abdullah login-aws.pem ubunutu@<bastian-Server-pi>:home/ubuntu<br></br>
is command say hoga ye kay hum bastian host pay connect kr kay jb ls karein gay tou udher bhi ye pari hogi.<br></br>
# Some imp thing about loadbalancer:<br></br>
Jb bhi load balancer use karein ge tou hum apni app ko load balabncer kay ip kay through access karein ge..ab load balancer traffic multiple instances/container pay bhej rha hoga aur haar instance ya container aik alaag port pay run hoga. let suppose is project may meray 2 instances hain aur load balancer nay traffic dono instances pay bhejni hai..tou instance 1 let suppose port 8001 pay run hoga aur instance 2 let suppose port 8002 pay run hoga..<br></br>

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

# Abishek answer:
There are multiple approaches like we can set rule at SG or at NACL level but most accurate approach is: To restrict outbound internet access for resources in one subnet, we can modify the route table associated with that subnet. In the route table, we can remove the default route (0.0.0.0/0) that points to an internet gateway. This would prevent resources in that subnet from accessing the internet. For the subnet where outbound internet access is required, we can keep the default route pointing to the internet gateway.<br></br>


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

# Q3: You have a VPC with a public subnet and a private subnet. Instances in the private subnet need to access the internet for software updates. How would you allow internet access for instances in the private subnet?

# Abhishek answer:
My answer is exactly same as abhishek answer. To allow internet access for instances in the private subnet, we can use a NAT Gateway or a NAT instance. <br></br>
We would place the NAT Gateway/instance in the public subnet and configure the private subnet route table to send outbound traffic to the NAT Gateway/instance. This way, instances in the private subnet can access the internet through the NAT Gateway/instance.<br></br>

# Q4: You have launched EC2 instances in your VPC, and you want them to communicate with each other using private IP addresses. What steps would you take to enable this communication?<br></br>
# Abhishek answer:<br></br>
 By default, instances within the same VPC can communicate with each other using private IP addresses. <br></br>
To ensure this communication, we need to make sure that the instances are launched in the same VPC and are placed in the same subnet or subnets that are connected through a peering connection or a VPC peering link. Additionally, we should check the security groups associated with the instances to ensure that the necessary inbound and outbound rules are configured to allow communication between them.<br></br>
# Same thing in my wording: <br></br>
If two instances are in same VPC and in same subnet that means they have same cidr block and have same subnet ip address range and if they have same subnet ip address range, they can easily communicate with each other but if they are in different subnet then we use VPC peering (In VPC peering one VPC can talk to another VPC with a link) basically we go to the route table and attach the endpoint of other vpc and similarly we will do the same in other vpc. just the route tables is update so one vpc can communicate with other vpc.<br></br>

# Q5: You want to implement strict network access control for your VPC resources. How would you achieve this?<br></br>

# Abhishek answer:<br></br>
My answer is exactly same as abhishek answer. To implement granular network access control for VPC resources, we can use Network Access Control Lists (ACLs). <br></br>
NACLs are stateless and operate at the subnet level. We can define inbound and outbound rules in the NACLs to allow or deny traffic based on source and destination IP addresses, ports, and protocols. By carefully configuring NACL rules, we can enforce fine-grained access control for traffic entering and leaving the subnets.<br></br>

# Q6: Your organization requires an isolated environment within the VPC for running sensitive workloads. How would you set up this isolated environment?

# Abhishek answer:<br></br>
To set up an isolated environment within the VPC, we can create a subnet with no internet gateway attached. <br></br>
This subnet, known as an "isolated subnet," will not have direct internet connectivity. We can place the sensitive workloads in this subnet, ensuring that they are protected from inbound and outbound internet traffic. <br></br>
However, if these workloads require outbound internet access, we can set up a NAT Gateway or NAT instance in a different subnet and configure the isolated subnet's route table to send outbound traffic through the NAT Gateway/instance.<br></br>

# Q7: Your application needs to access AWS services, such as S3 securely within your VPC. How would you achieve this?<br></br>

# Abhishek answer:<br></br>
To securely access AWS services within the VPC, we can use VPC endpoints. VPC endpoints allow instances in the VPC to communicate with AWS services privately, without requiring internet gateways or NAT gateways. <br></br>
We can create VPC endpoints for specific AWS services, such as S3 and DynamoDB, and associate them with the VPC. <br></br>
This enables secure and efficient communication between the instances in the VPC and the AWS services.<br></br>

# Q8: What is the difference between NACL and Security groups ? Explain with a use case ?<br></br>

# Abhishek answer:<br></br>
For example, I want to design a security architecture, I would use a combination of NACLs and security groups. At the subnet level, I would configure NACLs to enforce inbound and outbound traffic restrictions based on source and destination IP addresses, ports, and protocols. NACLs are stateless and can provide an additional layer of defense by filtering traffic at the subnet boundary.<br></br>
At the instance level, I would leverage security groups to control inbound and outbound traffic. Security groups are stateful and operate at the instance level. By carefully defining security group rules, I can allow or deny specific traffic to and from the instances based on the application's security requirements.<br></br>
By combining NACLs and security groups, I can achieve granular security controls at both the network and instance level, providing defense-in-depth for the sensitive application.<br></br>

# Q9: What is the difference between IAM users, groups, roles and policies ?<br></br>

# Abhishek answer:<br></br>
IAM User: An IAM user is an identity within AWS that represents an individual or application needing access to AWS resources. IAM users have permanent long-term credentials, such as a username and password, or access keys (Access Key ID and Secret Access Key). IAM users can be assigned directly to IAM policies or added to IAM groups for easier management of permissions.<br></br>
IAM Role: An IAM role is similar to an IAM user but is not associated with a specific individual. Instead, it is assumed by entities such as IAM users, applications, or services to obtain temporary security credentials. IAM roles are useful when you want to grant permissions to entities that are external to your AWS account or when you want to delegate access to AWS resources across accounts. IAM roles have policies attached to them that define the permissions granted when the role is assumed.<br></br>
IAM Group: An IAM group is a collection of IAM users. By organizing IAM users into groups, you can manage permissions collectively. IAM groups make it easier to assign permissions to multiple users simultaneously. Users within an IAM group inherit the permissions assigned to that group. For example, you can create a "Developers" group and assign appropriate policies to grant permissions required for developers across your organization.<br></br>
IAM Policy: An IAM policy is a document that defines permissions and access controls in AWS. IAM policies can be attached to IAM users, IAM roles, and IAM groups to define what actions can be performed on which AWS resources. IAM policies use JSON (JavaScript Object Notation) syntax to specify the permissions and can be created and managed independently of the users, roles, or groups. IAM policies consist of statements that include the actions allowed or denied, the resources on which the actions can be performed, and any additional conditions.<br></br>

#  Q10: You have a private subnet in your VPC that contains a number of instances that should not have direct internet access. However, you still need to be able to securely access these instances for administrative purposes. How would you set up a bastion host to facilitate this access?<br></br>

# Abhishek answer:<br></br>
To securely access the instances in the private subnet, you can set up a bastion host (also known as a jump host or jump box). The bastion host acts as a secure entry point to your private subnet. Here's how you can set up a bastion host:<br></br>
Create a new EC2 instance in a public subnet, which will serve as the bastion host. Ensure that this instance has a public IP address or is associated with an Elastic IP address for persistent access.<br></br>
Configure the security group for the bastion host to allow inbound SSH (or RDP for Windows) traffic from your IP address or a restricted range of trusted IP addresses. This limits access to the bastion host to authorized administrators only.<br></br>
Place the instances in the private subnet and configure their security groups to allow inbound SSH (or RDP) traffic from the bastion host security group.<br></br>
SSH (or RDP) into the bastion host using your private key or password. From the bastion host, you can then SSH (or RDP) into the instances in the private subnet using their private IP addresses.<br></br>

# DAY 9 S3 (Simple Storage Service):<br></br>
It is the very easy and simple service to learn in aws. It solves the very basic problem of storage that everyone co-relates. Let suppose we are using a phone or laptop and we ran out of storage then what we can do? We buy a harddisk pendrive of some 500GB or 1TB etc but organizations have a very large data, databases, data dumps, application logs, excel files, csv file and many other which can’t be store in some TB harddisk etc so they need some storage solution and as we discussed previously organizations are moving towards public cloud and how aws solved this issue.. Answer is aws s3 service.<br></br>
The major success behind this like why s3 become so popular lie’s in the single number (11 9’s) 99.99999999999<br></br>

Q: What is S3 and what are its characteristics?<br></br>
A: S3 is a simple storage service which has the following characteristics:<br></br>
Highly available, scalable, cost effective, secure and performance.<br></br>
It is a cloud storage service provided by aws.<br></br>
S3 allows you to store and retrieve any amount of data anywhere from the web.<br></br>

What you can store in these s3? Like You may say kay my laptop storage is full because i download many movies in it and my phone storage is full because I saved a lot of photos in it but what kind of files, data an organization have? And what kind of things are store in s3?<br></br>

In general, s3 doesn’t have any restriction you can store videos, photos, files, reports, excel sheets etc but as devops engineer you sometimes need to store application logs for some 30 days or sometimes organization needs to store some huge databases. Let’s take an example of flipkart.com. Fipkart have a huge database that contains user information like the information of users who uses flipkart for last 30 days and organization do backup of these databases/information as well...even if we took on single dump of this information or even do a backup of this information/databases it took almost 6-7TB. So it’s a big problem then amazon comes into a picture and said no problem as you move to a public cloud then this problem is solved by myself (my service of s3 is able to do so). S3 is the second service that aws introduced which clearly shows how much important this storage issue was at that time.<br></br>

Anything that you upload on S3 you can basically access that object using HTTP protocol. So let’s say you created a bucket and name of the bucket is demo-aj-january08 then we can access the content inside the bucket using the HTTP protocol and also add the api of the bucket before the bucket name. S3 is a globally accessible service means you can put your logs files and databases anywhere in the world and you can access it from anywhere in the world. Let say if you put a movie in s3 bucket and share its url then anyone in the world can access it.<br></br>

Anything that you upload on S3 you can basically access that object using HTTP protocol. So let’s say you created a bucket and name of the bucket is demo-aj-january08 then we can access the content inside the bucket using the HTTP protocol and also add the api of the bucket before the bucket name. S3 is a globally accessible service means you can put your logs files and databases anywhere in the world and you can access it from anywhere in the world. Let say if you put a movie in s3 bucket and share its url then anyone in the world can access it.<br></br>

Bucket in aws is very simple concept. We understand this with the following easy example;<br></br>
When we create ec2 in aws we basically get the virtual machine or compute instance. Similarly, if we go to the s3 service what we get from the s3 service? We get the s3 bucket and inside that bucket we can store the information that’s why we call it bucket and this bucket don’t have any restrictions like how much data you can store? What kind of data you can store? Technically you can store Tbs of data like 100 tBs with very less cost.<br></br>

As s3 bucket is globally accessible so you have to make a bucket with a unique name. The name not be unique wrt to your aws account. it should be unique wrt to all aws accounts across the world because s3 is a globally accessible service.. so the nomenclature that abhisek said to follow is: appname-featurename-environment-company domain (e.g; website-payments-prod-example.com)..<br></br>
Ab jo dropdown menu hota ha right top corner pay jidher say hum region select kartey hain like Stockholm, N.Virginia.. S3 kay case may udher global likha a rha ha aur create bucket waley interface may bucket name kay baad AWS region ka block ha us may humney region select karna ha ye kia scene ha? is concept ko samjho.. S3 buckets are scoped in a region like we create ec2 instance only where we put it in a region but only difference is contents in s3 is globally accessible..means s3 bucket ko ma kisi aik specific region may bnao ga but s3 bucket ka content globally accessible ha is liye hum isey globally accessible boltey hain..(not cnfrm)<br></br>

# Q: We said s3 is a a globally accessible service but we select a region while creating s3 bucket.. Whats the reason of this? explain in easy wording?<br></br>
Short answer<br></br>

S3 is a global service, but your data must live in one specific region.<br></br>

Easy explanation with an example 🌍<br></br>

Think of Amazon S3 like a global bank:<br></br>

The bank (S3 service) is available worldwide<br></br>

But when you open a locker (S3 bucket), you must choose one branch (region)<br></br>

Even though you can access your locker from anywhere, the locker physically exists in one branch only.<br></br>

Why AWS asks you to choose a region when creating a bucket?<br></br>

Because:<br></br>

1️⃣ Data has to be stored somewhere physically<br></br>

AWS has data centers in different regions (Mumbai, Virginia, London, etc.).<br></br>

When you select a region:<br></br>

Your bucket’s data is stored in that region’s data centers<br></br>

2️⃣ Performance (faster access)<br></br>

If your users or applications are in India:<br></br>

Choosing ap-south-1 (Mumbai) gives faster access<br></br>

Less distance = less delay (latency)<br></br>

3️⃣ Cost control 💰<br></br>

Data transfer within the same region is cheaper<br></br>

Cross-region data transfer can cost more<br></br>

4️⃣ Legal & compliance reasons 📜<br></br>

Some companies must keep data:<br></br>

In a specific country or region<br></br>

AWS enforces this by region-based buckets<br></br>

Why do we still call S3 a global service?<br></br>

Because:<br></br>

You don’t create S3 separately in each region<br></br>

The S3 service is managed globally by AWS<br></br>

You can access your bucket from anywhere in the world, even though it lives in one region<br></br>

One-line exam/interview answer 🧠<br></br>

Amazon S3 is a global service because it can be accessed from anywhere, but each bucket is created in a specific region to store data physically, improve performance, reduce cost, and meet compliance requirements.<br></br>

Let suppose you add some data in s3 bucket. Now if that data gets deleted from your local system like laptop or pc then still you have it in your s3. Everything in s3 is called as an object. Its either videos, photos, movies, db etc they all called as an object.
Now take a scenario kay let suppose your availability zone gets down in which you have your s3 and we already said that s3 is highly available and we have store data dumps and confidential data in it so what happens if s3 gets down. It’s a concerning issue if organization confidential data gets down. The answer lies in the number 99.99999999999. AWS claims that if you add 1 billion objects in s3 over a period of 100 years then there’s a chance kay only 1 object gets deleted this is how much s3 service is reliable. The reason behind this relability is kay in one region there are multiple availability zones and in each availability zones there are multiple data centers so aws replicates this bucket kay if one az gets down, its still available from other az as well.  <br></br>
# Advantages of s3:<br></br>
The following is the advantages of s3:<br></br>
Scalability and Durability<br></br>
Availability<br></br>
Security<br></br>
Cost Effective <br></br>
Performance<br></br> 
# Performance: <br></br> 
If you create s3 in a region nearby you then you can quickly access the content, download it and use it and quickly upload it and one more thing regarding performance is kay if you want to upload some file and that file is around 400TB or while upload you face some power cut issue or internet issue and upload takes some days  then what happens? AWS comes with a concept called multi-part upload  in this you divide the file to upload in chunks like you divide into multiple 100MB chunks.<br></br> 
Even in multi-part upload if there’s some mishap in uploading aws will retry that process and it will continue your upload thing.<br></br> 
# Durability:<br></br> 
(S3 is 99.99999999999) percent reliable and durable<br></br> 
# Scalability:<br></br> 
You can store alomost unlimited data in a single bucket. However, one object should not be more than 5Tb which is a very huge amount. If you want to upload file more than 5tb then you have to break your file.<br></br> 
# Tip:<br></br> 
Choose multi-part upload to upload an object if the size of an object is huge.<br></br> 
# Security:<br></br> 
Organizations can store their application logs and data dumps in s3 so they must ask you for the security. AWS focuses much more on security. Aws provide organization with a lot of security option like you can upload your data in s3 bucket with encrtypion there are two things encryption at rest and encryption at transit. Aws supports both. AWS also has ACLs(Access control lists, bucket policies like you can restrict who can access the objects, we can also lock the objects in buckets). We can also enable access logging to capture detailed records of requests made to your s3 bucket.<br></br> 
# Cost Effective<br></br> 
S3 bucket is very cheap but it also depends on the storage class that you are using. Read more about s3 storage classes from abgishek document of day 9 and from aws documentation.<br></br> 
very cheap s3 service is S3 Glacier Deep Archive.<br></br> 

# Abhishek concept of s3 versioning:<br></br> 
We can use multiple things in s3 buckets..Let suppose we add application log files on day1, next day I added the log file of same application and on the third day i added the logs of same application…Take an example of git for better understanding let suppose we have a code file, next day the code file got updated and third day the developer said the file..that was updated on yesterday was wrong I want my code of first day…so you simple revert and make that version available same things goes with  s3 bucket it also works on versioning but if versioning is disabled then it completely replaces or overrides the previous file and won’t keep track of any record or history but If versioning is enabled in s3 bucket then multiple versions of same thing is created. Learn gpt perspective for better underst<br></br> 

# Q: What is s3 bucket versioning concept? Explain this concept in easy wording with real-life examples.<br></br> 
Amazon S3 bucket versioning is a feature that keeps multiple versions of the same file in an S3 bucket instead of replacing or permanently deleting it.<br></br> 
Think of it as automatic “Save History” for files 📂<br></br> 
________________________________________<br></br> 
Simple definition<br></br> 
S3 Versioning = S3 remembers every change made to an object (file).<br></br> 
Whenever you:<br></br> 
•	Upload a new file with the same name<br></br> 
•	Modify a file<br></br> 
•	Delete a file<br></br> 
👉 S3 keeps the old version instead of losing it<br></br> 
________________________________________<br></br> 
Real-life example (very easy)<br></br> 
📝 Example 1: Google Docs / MS Word history<br></br> 
You write a document:<br></br> 
•	Version 1: Draft<br></br> 
•	Version 2: Added introduction<br></br> 
•	Version 3: Final copy<br></br> 
Even if you make a mistake, you can go back to any previous version.<br></br> 
➡️ S3 versioning works the same way<br></br> 
________________________________________<br></br> 
How it works in S3 (simple flow)<br></br> 
Case 1: Upload same file again<br></br> 
You upload:<br></br> 
resume.pdf<br></br> 
Then you upload another resume.pdf (updated one).<br></br> 
With versioning ON:<br></br> 
•	S3 stores both files<br></br> 
•	Each gets a unique version ID<br></br> 
resume.pdf (version 1)<br></br> 
resume.pdf (version 2)<br></br> 
Nothing is overwritten ❌<br></br> 
________________________________________<br></br> 
Case 2: Delete a file<br></br> 
You delete resume.pdf.<br></br> 
With versioning ON:<br></br> 
•	File is not actually deleted<br></br> 
•	S3 adds a delete marker<br></br> 
You can still restore the file later ✔️<br></br> 
________________________________________<br></br> 
Case 3: Accidentally changed data<br></br> 
You updated a file with wrong data.<br></br> 
With versioning:<br></br> 
•	Just rollback to the previous version<br></br> 
•	No data loss 👍<br></br> 
________________________________________<br></br> 
Real-life analogy: School notebook 📘<br></br> 
Imagine:<br></br> 
•	You write with pencil<br></br> 
•	Teacher asks you to erase something<br></br> 
•	You regret it later<br></br> 
❌ Without versioning → Content is gone<br></br> 
✔️ With versioning → You have photocopies of every page change<br></br> 
________________________________________<br></br> 
Why versioning is useful (important benefits)<br></br> 
✔️ Protects from accidental deletion<br></br> 
✔️ Protects from overwriting files<br></br> 
✔️ Helps in data recovery<br></br> 
✔️ Required for backup & compliance<br></br> 
✔️ Works with S3 replication & backups<br></br> 
________________________________________<br></br> 
Important points to remember<br></br> 
•	Versioning is set at bucket level<br></br> 
•	Once enabled, it cannot be disabled, only suspended<br></br> 
•	Each version costs storage money<br></br> 
•	Old versions stay until you delete them manually or via lifecycle rules<br></br> 
________________________________________<br></br> 
One-line summary<br></br> 
S3 bucket versioning keeps a history of all file changes so you can recover deleted or overwritten data anytime.<br></br> 

# Q: If versioning is disabled then what happened if i upload the same file? or same file with a little bit changes in it?
When S3 Versioning is DISABLED<br></br> 
Rule (very important):<br></br> 
S3 keeps only ONE copy of a file. No history.<br></br> 
________________________________________<br></br> 
Case 1: Upload the same file again (same name)<br></br> 
Example:<br></br> 
You upload:<br></br> 
report.pdf<br></br> 
Later, you upload another report.pdf (same file or updated one).<br></br> 
What happens?<br></br> 
•	The new file replaces the old file<br></br> 
•	The old file is permanently lost<br></br> 
•	❌ No backup<br></br> 
•	❌ No rollback<br></br> 
📌 S3 doesn’t care whether the content changed or not — filename is what matters<br></br> 
________________________________________<br></br> 
Case 2: Upload same file with small changes<br></br> 
Example:<br></br> 
•	Old file: salary.xlsx (January data)<br></br> 
•	New file: salary.xlsx (February data)<br></br> 
What happens?<br></br> 
•	S3 overwrites the old file<br></br> 
•	Only the latest version exists<br></br> 
•	You cannot recover January data<br></br> 
________________________________________<br></br> 
Case 3: Delete a file<br></br> 
Example:<br></br> 
You delete image.jpg.<br></br> 
What happens?<br></br> 
•	File is permanently deleted<br></br> 
•	❌ No delete marker<br></br> 
•	❌ No restore option<br></br> 
________________________________________<br></br> 
Simple comparison table<br></br> 
Action	Versioning OFF	Versioning ON<br></br> 
Upload same filename	Old file overwritten	New version created<br></br> 
Upload changed file	Old data lost	Old version preserved<br></br> 
Delete file	Permanently deleted	Delete marker added<br></br> 
Recover old data	❌ Impossible	✔️ Possible<br></br> 
________________________________________<br></br> 
Real-life example 🧠<br></br> 
Without versioning = Writing on a whiteboard<br></br> 
•	You erase old content<br></br> 
•	It’s gone forever<br></br> 
With versioning = Writing in a notebook<br></br> 
•	Old pages stay<br></br> 
•	You can go back anytime<br></br> 
________________________________________<br></br> 
One-line summary<br></br> 
When versioning is disabled, uploading a file with the same name simply replaces the old file — no history, no recovery.<br></br> 
# Tags in s3 buckets:<br></br> 
It is basically used for identifying. We have multiple s3 buckets across multiple accounts so we used tags if someone asks kay I want all the buckets that store the file for transaction project so at that point tags become useful.<br></br> 
# Object Locking:<br></br> 
Once we upload the object in bucket we lock it so no one can access it. Its for security reasons. We can also use the bucket locking concept if someone wants to override the bucket/object and we want to restrict it then we use bucket locking. Object locking doesn't applicable on the pre-existing objects..like mainey aik bucket may aik object rakha hua ha aur may us kay kuch time baad object locking wala feature enable karta hu tou hoga ye kay ab ma jb koi new bucket aur new object bnao ga us pay object locking apply ho gi..already existing object pay object locking work nhi karey ga<br></br> 
# Default Encryption:<br></br> 
S3 recently added the default encryption means now objects are bydefault encrypted.<br></br> 
# Access Logging:<br></br> 
Bydefault it is disabled, It is used so we can check who can access our bucket, what kind of actions they are performing and also we can restrict them as well.<br></br> 
# S3 Bucket Demo1 on Permission:<br></br> 
Let suppose you are working in an organization as a devops engineer and in that organization you create IAM users in which you set a policy kay all people in organization have full access to s3.. Now everyone in an organization have full access to s3 but there's a one bucket which contains very sensitive data and you want to restrict other people to access that bucket although you give all access in IAM policy but being a bucket owner you can restrict the access for that specific bucket by setting the permissions (in permissions you add some json which means you restrict all user except you to access the bucket). So, if you misconfigured the policy at IAM time you can still restrict the access by setting the bucket permissions. This is just one usecase you can work on multiple usecases like this. Try with object locking policy etc. DO this on weekend<br></br>
In order to host static website we need to do 3 things, first enable static website hosting option, then disable block all public access, add then bucket policy by allowing s3:GetObject and<br></br>
S3 is very cheap to host a static website as compared to other hosting platforms. <br></br>
If we use rich JavaScript like the javascript code in which apis are used then we use something called CORS which will be discussed in detail when we do Cloudfront or CDN <br></br>

# Object Lock in S3 bucket<br></br>
# 🧠 Simple definition (one line)<br></br>

S3 Object Lock prevents files from being deleted or changed for a fixed time — even by admins.<br></br>

# 🧩 Real-life example (best way to understand)<br></br>
🗄️ Bank locker example<br></br>

Imagine a bank locker:<br></br>

You put important documents inside<br></br>

You tell the bank:<br></br>

“Do NOT allow anyone to remove or change these documents for 5 years”<br></br>

Even:<br></br>

bank employees ❌<br></br>

branch manager ❌<br></br>

you ❌<br></br>

No one can touch it until 5 years pass<br></br>

➡️ That’s Object Lock.<br></br>

# 🧾 Another real example: Exam papers<br></br>

A university stores exam papers:<br></br>

Once uploaded, they must:<br></br>

not be changed<br></br>

not be deleted<br></br>

For 10 years (legal requirement)<br></br>

Object Lock ensures:<br></br>

no cheating<br></br>

no accidental deletion<br></br>

full compliance<br></br>

# 🧩 How Object Lock works in S3 (simple words)<br></br>

When Object Lock is ON:<br></br>

Files become write-once<br></br>

You cannot delete<br></br>

You cannot overwrite<br></br>

Only after time expires → file is normal again<br></br>

# 🔒 Two Object Lock modes (very important)<br></br>
# 1️⃣ Governance Mode (soft lock)<br></br>

👨‍💼 Example:<br></br>

Company rule: “Keep logs for 1 year”<br></br>

Admins can override with special permission<br></br>

✔ Protects from mistakes<br></br>
❌ Can be overridden by high-level admin<br></br>

# 2️⃣ Compliance Mode (hard lock 🔥)<br></br>

🏛️ Example:<br></br>

Legal / government records<br></br>

Even root user CANNOT delete<br></br>

✔ Strongest protection<br></br>
✔ Meets legal compliance<br></br>
❌ Cannot be bypassed<br></br>

⏱️ Retention period<br></br>

You must set:<br></br>

1 day<br></br>

1 year<br></br>

10 years<br></br>

or a specific date<br></br>

Example:<br></br>

“Lock this file until 1 Jan 2030”<br></br>

# 2️⃣ Important Point Regarding Object Lock<br></br>
Object Lock can ONLY be enabled when creating a new bucket<br></br>

You cannot enable it on an existing bucket<br></br>

Versioning is required (AWS enables it automatically)<br></br>
Once Amazon S3 Object Lock is enabled, you can't disable Object Lock or suspend Versioning for the bucket.<br></br>

# DAY 10 AWS CLI<br></br>
Till now from Day 0 to Day 9 we used AWS UI. What this mean? means when we want to create VPC or EC2 instance or anything else we simply go to aws console and login to our account and create the desired things but let suppose one day when i enter in my office and logged in to my system i saw that my jira is filled with multiple tickets like create 10 EC2 instances for team1, 15 VPCs with desired configuration for team 2 and 500 s3 buckets with desired configuration for team 3. So when i maunally create all these things with UI it takes a lot of time..my day end but work doesn't complete so inshort AWS UI is not automation friendly..Being a devops engineer our primary responsibiltity is infrastructure management/automation but when we do with UI it takes a lot of time which means its not a automation friendly so what's the solution for this problem? Solution for this problem is AWS API (Application Programming Interface). AWS API is automation friendly and with this we can programmatically create delete and manage our aws resources. Let suppose we are assigned with a task to create 50 EC2 instances so instead of doing it manually via a UI we simply write a shellscript or any script and invoke that api in the script through which we can create, manage and delete the resources programmatically in a quick fashion. We also add the necessary credentials for login in our script as well (not cnfrm).<br></br> 
In order to use aws api, there are bunch of tools in market but most common tools are aws cli, cloudformation, terrafoam, aws cdk (cloud/code development kit)...terrafoam, cdk and cloudformation are also called as Iac. We use these tools for infrastructure automation on aws. <br></br>
In this section we discuss about awscli. AWS CLI is a python-based utility or simply we can say it is a python program designed by aws engineers itself and aws itself supports it. In order to manage resources on aws we use aws cli and add some parameter and variables to it like initially we add some credentials(username & password) to authenticate to aws and then we add sone parameter like bucket versionion or other to create s3 bucket on aws or anyother resource as well.<br></br>
There are two ways to access any application like one with UI and other with API. Here we take an example of aws. We can access aws through UI or through API. If aws expose its api then we can manage or create resources like this way we just add the following line in our script/code along with necessary parameters.<br></br>
POST api.aws.com/s3/create <br></br>
If we are python or anyother developer we use this api in our code using request model or any other model and also add some parameters in code like bucket versioning or bucket name then our resource is created on aws<br></br>
Inshort, scene ye hota ha kay jb apney api kay through resource creation, deletion, ya management karwani hoti ha tou jo app owner hota ha wo kehta ha ye meri api ha is ko jo bhi HTTP request ha POST ya GET ki us kay sath use kro aur jo bhi parameters wagera denay hain sath wo apney program may add kr do aur phir tumhara resource create ho jye ga..(not cnfrm)
Now you might think kay manage resources via api is complex you first understand how to use api in code and then understand how to use HTTP method and many other things but you are wrong... manage resources via api or prgrammatically is not difficult because AWSCLI, Terrafoam and CFT(Cloud Formation Template) provides an abstraction over this. What this mean? It means AWScli, terrafoam and CFT said, ohh devops engineer no need to worry.. you don't have to do any programming we can do all this stuff for you just have to use it and then devops engineer said how i can use this? then they said lets assume aws cli said i creation a python application or python program for you..you just need to install that program and run it using the following way [./aws <rersources-that-you-want-to-create> <parameter for that resource>] e.g: you want to create s3 bucket with name mys3 so what you can do? you simple do [./aws s3 mys3] now this command convert your request into an api call and that api call is send to an aws and in result you will get the s3 bucket with name mys3. All you need to install program/application and read/understand the awscli docs to get a better understanding kay how you create different resources and how you can pass the parameters <br></br>  
inshort, AWS CLI acts as a layer between User and API. User<->CLI<->API <br></br>
As we said AWSCLI, Terrafoam and CFT are providing the same purpose like infra management via api (not cnfrm). If aws cli provides the same purpose then why there's a need for the terafoam and cft? AWS cli is good for the quick usecase like your manager comes and said Abdullah tell me the total number of s3 buckets that we created..so i quickly go to the terminal and write this command [./aws s3 ls] and all my s3 buckets are listed (The same thing if i do with ui takes a time like first i go to the console, enter my credentials and go to s3..but with api i quickly see it with just one command) but for the large infrastructure where we have to manage many aws resources or where multiple stacks are stack over each other then we have to use terrafoam, and cft like if the same manager come and said abdullah make a vpc and 2 ec2 instances then its very difficult and time taking to make make it with cli so that's why cli is only good for quick usecases...<br></br>
Terrafoam and cft provide api as a code as well for code review.. this thing is out of context for today's lecture we will discuss it later. <br></br>
Inshort aws cli is good for quick usecase but for large infrastructure management/creation we have to use terrafoam and cft etc <br></br>
Inorder to install aws cli, you must need to install python before installation of aws cli bcz it is a python utility (not cnfrm)<br></br>
Now i setup/install aws cli on my system but ab aws cli ko kaisey pta chaley ga kay us nay kis aws account say connect hona ha. For this we wrire a command [aws configure] and then we are asking for few things like aws access key, aws secret key, default region, and output format...you may consider aws access key and security key as a username and password...why we need access key? in order to use/access APIs we need either API tokens or access keys so that's why here we use access keys and it is not recommended to use aws cli or use api as a root user..always login from iam user to use aws cli or manage resources via api...<br></br>
From whhere we get access keys, security keys? click on account id then go to security section and then create access keys and security keys <br></br>

# DAY 11 Iac With CFT <br></br>
Cloud Formation Templates are templates used for cloud formation for aws i.e managing, creating, deleting resources on aws. There are multiple tools that does the same thing as well..as we discussed before aws cli.. then what's the difference between aws cli and cft? answer is cft follows the principle of iac but aws cli doesnot follow the principle of iac.. Iac stands for (Infrastructure as code) like you do coding to make and mange the infrastructe on cloud..Aws cli is also good for quick usecases and we also write commands in aws cli to make and manage infra but aws cli does not follow the principles of iac that makes cft a powerful tool to manage infra on cloud.<br></br>
# Principles of Iac <br></br>
Let suppose you create some Iac tool. The principle said that tool act as a middleman between one or multiple cloud providers. Like if we use cft then it only supports aws and act as middleman between user and only one cloudprovider(aws) in the same way azure resource manager also act as a middleman between user and single cloudprovider but in case of terrafoam which is also an iac tool. It acts as a middle man between user and multiple cloud providers.. so it all depends on the implementation of the tool. user <-> iac tool <-> cloudprovider. <br></br>
Q: How all this process works?<br></br>
User submits a template which is a json or yaml file with some decelration and version and the iac tool then convert this yaml and json file into the language that is understand by cloud providers and cloud providers usually understand API call because cloud providers are also an application(aws/azure).. so, iac tool converts yaml and json file into api call.<br></br>
Now we discuss other principles of iac.. other principles are versioning and decleration.. Versioning is just like git like you store your template somewhere at git repo or any s3 bucket and you can easily go to previous 10 days version... Now we discuss about declerative..we use one line for declarative "What you see is what you have" means whatever your write in template is available on aws..by just looking at the tempalte you came to know that what resources are present on aws (not cnfrm)<br></br>
Q: if interviewer asked kay when to use aws cli and when to use cft ? Ans is when we need short or quick actions like list of s3 buckets then we use aws cli and if we want to create and manage resources then we go for aws cft..<br></br>
# Format of CFT <br></br>
CFT supports both yaml and json format but if you ask abhishek kay which format to use he said yaml if you are new to cft because we can add comments in yaml but we don't add comments in json..also yaml works on proper indention and easy to understand but json works on bracket and difficult to understand <br></br>
# Features of CFT <br></br>
The main feature of CFT is infrastructure creation but it have other features as well like Drift Defection.. What is drift detection? Let suppose you create EC2 and s3 using cft but next day your teammate visits aws ui console and he unintentionally change some settings like he disable the bucket versioining but previously when we create s3 with cft at that time bucket versioning is enable. so, now you are unable to keep different versions and when you see this issue and visit cft then there's an option called drift detection when you click on this it backtrace and let you know who changes the setting..so, you can easily identify and adjust the permissions of that person accordingly..<br></br>
Now we understand that kay we have to write yaml files which is our cloud formation template but we write this on our local system then how we can move these templates to cloud? When we go to cft service on aws then there's an option called stacks..when we go to stacks and click an option named "create stack" then we actually move these yaml templates from our local system to aws <br></br> 
The mandatory thing in cft yaml file is resources section...Without resources section we are unable to make cft.. rest of the other things are optional..<br></br> 
In yaml file following things are present..version,description,metadata,parameters,rules,mapping,conditions,resources(mandotry thing),output <br></br>
AWS offical documentation on Cloud Formation Template is recommended <br></br>

# What is AWS CloudFormation (CFT)?<br></br>

AWS CloudFormation is a service that helps you create AWS resources automatically using a template file.<br></br>

👉 Instead of clicking in the AWS console again and again,<br></br>
👉 you write everything once in a template,<br></br>
👉 AWS reads it and creates resources for you.<br></br>

Think of it as:<br></br>

“Infrastructure as Code”<br></br>

That means:<br></br>

Your servers<br></br>

Databases<br></br>

Networks<br></br>
are written as code (YAML or JSON)<br></br>

# What is a CloudFormation Template?<br></br>

A CloudFormation Template is a text file written in:<br></br>

YAML (recommended & easy)<br></br>

or JSON<br></br>

This file tells AWS:<br></br>

What resources to create<br></br>

How they should be connected<br></br>

What values to use<br></br>

# Basic Structure of a CloudFormation Template<br></br>

A CloudFormation template has sections.<br></br>

Not all sections are mandatory, but these are the most common:<br></br>

AWSTemplateFormatVersion<br></br>
Description<br></br>
Parameters<br></br>
Mappings<br></br>
Conditions<br></br>
Resources<br></br>
Outputs<br></br>

We will explain each one clearly 👇<br></br>

#  1️⃣ AWSTemplateFormatVersion<br></br>
What it is:<br></br>

Tells AWS which version of CloudFormation template you are using<br></br>

Is it mandatory?<br></br>

❌ No, but recommended<br></br>

# Example:<br></br>
AWSTemplateFormatVersion: '2010-09-09'<br></br>


👉 AWS currently uses this date format.<br></br>

# 2️⃣ Description<br></br>
What it is:<br></br>

A simple text explanation of what your template does<br></br>

# Rules:<br></br>

Must be one line<br></br>

Cannot use line breaks<br></br>

# Example:<br></br>
Description: This template creates an EC2 instance with a security group<br></br>

# 3️⃣ Parameters<br></br>
What are Parameters?<br></br>

Parameters let you ask the user for input.<br></br>

Instead of hardcoding values, you can ask:<br></br>

Instance type?<br></br>

Key pair name?<br></br>

Environment (dev/prod)?<br></br>

Why use Parameters?<br></br>

✔ Reusable templates<br></br>
✔ Flexible<br></br>
✔ Easy to change values<br></br>

# Example Parameter:<br></br>
Parameters:<br></br>
  InstanceType:<br></br>
    Type: String<br></br>
    Default: t2.micro<br></br>
    Description: EC2 instance type<br></br>

# Explanation:<br></br>

InstanceType → parameter name<br></br>

Type: String → value must be text<br></br>

Default → value used if user doesn’t give one<br></br>

Description → help text<br></br>

# Common Parameter Types:<br></br>
Type	Meaning<br></br>
String	Text value<br></br>
Number	Numeric value<br></br>
AWS::EC2::KeyPair::KeyName	EC2 key pair<br></br>
AWS::EC2::VPC::Id	VPC ID<br></br>
CommaDelimitedList	List of values<br></br>
# 4️⃣ Mappings<br></br>
What are Mappings?<br></br>

Mappings are fixed values based on conditions like region.<br></br>

# Example:<br></br>

AMI ID for us-east-1<br></br>

Different AMI for ap-south-1<br></br>

User cannot change mapping values.<br></br>
Example:<br></br>
Mappings:<br></br>
  RegionMap:<br></br>
    us-east-1:<br></br>
      AMI: ami-0abcdef123<br></br>
    ap-south-1:<br></br>
      AMI: ami-0123456789<br></br>

How to use it:<br></br>
ImageId: !FindInMap [RegionMap, !Ref AWS::Region, AMI]<br></br>


👉 AWS finds the correct AMI based on region.<br></br>

# 5️⃣ Conditions<br></br>
What are Conditions?<br></br>

Conditions let you create resources only if a condition is true.<br></br>

# Example:<br></br>

Create resource only in prod<br></br>

Enable backup only if user says “yes”<br></br>

# Example:<br></br>
Parameters:<br></br>
  Environment:<br></br>
    Type: String<br></br>
    Default: dev<br></br>

# Conditions:<br></br>
  IsProd: !Equals [!Ref Environment, prod]<br></br>

Use Condition in a resource:<br></br>
Condition: IsProd<br></br>

# 6️⃣ Resources (MOST IMPORTANT)<br></br>
What is Resources?<br></br>

This section is where you actually create AWS resources.<br></br>

👉 Without this section, nothing is created.<br></br>

# General Format:<br></br>
Resources:<br></br>
  LogicalName:<br></br>
    Type: AWS::Service::Resource<br></br>
    Properties:<br></br>
      PropertyName: value<br></br>

# Example: Create EC2 Instance<br></br>
Resources:<br></br>
  MyEC2Instance: //This is just a logical name you can write anything here<br></br>
    Type: AWS::EC2::Instance<br></br>
    Properties:<br></br>
      InstanceType: !Ref InstanceType<br></br>
      ImageId: ami-0abcdef123<br></br>
      KeyName: my-key<br></br>

# Explanation:<br></br>

MyEC2Instance → logical name (used inside template)<br></br>

Type → resource type from AWS<br></br>

Properties → settings of the resource<br></br>

# Common Resource Types:<br></br>
Resource	Type<br></br>
EC2	AWS::EC2::Instance<br></br>
S3	AWS::S3::Bucket<br></br>
IAM Role	AWS::IAM::Role<br></br>
Security Group	AWS::EC2::SecurityGroup<br></br>
RDS	AWS::RDS::DBInstance<br></br>
# 7️⃣ Outputs<br></br>
What are Outputs?<br></br>

Outputs show useful values after stack creation.<br></br>

# Example:<br></br>

EC2 Public IP<br></br>

Load Balancer DNS name<br></br>

S3 bucket name<br></br>

# Example:<br></br>
Outputs:<br></br>
  InstanceId:<br></br>
    Description: EC2 Instance ID<br></br>
    Value: !Ref MyEC2Instance<br></br>

# Important CloudFormation Functions (Easy)<br></br>
# 🔹 !Ref<br></br>

Gets value of:<br></br>

Parameter<br></br>

Resource ID<br></br>

InstanceType: !Ref InstanceType<br></br>

# 🔹 !GetAtt<br></br>

Gets attribute of a resource<br></br>

!GetAtt MyEC2Instance.PublicIp<br></br>

# 🔹 !Sub<br></br>

Used for string substitution<br></br>

!Sub "My instance is in ${AWS::Region}"<br></br>

# Full Simple CloudFormation Template Example<br></br>
AWSTemplateFormatVersion: '2010-09-09'<br></br>
Description: Simple EC2 creation using CloudFormation<br></br>

Parameters:<br></br>
  InstanceType:<br></br>
    Type: String<br></br>
    Default: t2.micro<br></br>

Resources:<br></br>
  MyEC2:<br></br>
    Type: AWS::EC2::Instance<br></br>
    Properties:<br></br>
      InstanceType: !Ref InstanceType<br></br>
      ImageId: ami-0abcdef123<br></br>

Outputs:<br></br>
  EC2Id:<br></br>
    Value: !Ref MyEC2<br></br>

# How CloudFormation Works (Flow)<br></br>

1️⃣ Write template (YAML/JSON)<br></br>
2️⃣ Upload to CloudFormation<br></br>
3️⃣ Create Stack<br></br>
4️⃣ AWS creates resources<br></br>
5️⃣ Stack manages everything<br></br>

# Benefits of CloudFormation (From AWS Docs)<br></br>

✔ Infrastructure as Code<br></br>
✔ Version control<br></br>
✔ Easy rollback<br></br>
✔ Automation<br></br>
✔ Repeatable & safe deployments<br></br>

# Official AWS Documentation Reference (Recommended)<br></br>

You can search these in AWS Docs:<br></br>

CloudFormation Template Anatomy<br></br>

AWS Resource and Property Types Reference<br></br>

Intrinsic Functions<br></br>

(These are exact AWS documentation topics)<br></br>

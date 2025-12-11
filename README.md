# Aws
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


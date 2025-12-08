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

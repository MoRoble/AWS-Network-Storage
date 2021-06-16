# AWS-Network-Storage

### Network Storage
##### Overview
I am pleased to submit this outline for migration of Elastic Files System at Hodan School. My proposal is based on the school required upgrade due to staff are working from home. The alternative is when staff are fully back on site to upgrade this plan to migrate to local on-premises server so that shared folder will be mounted to all devices in the school and all staff user profiles end to end.

#### Elastic File System

Elastic File System (EFS) is Amazon’s way of allowing businesses to share file data from multiple EC2’s or on-prem instances simultaneously. EFS is an elastic and serverless service. It automatically grows and shrinks depending on the file storing needs of your business without you having to provision or manage it.

As part of this project on upgrading Hodan Shcool Network Storage we have chosen Amazon EFS to a way more flexible, elastic, Strong consistency, concurrent accessibility, file locking and durable feautures. Currently, they have shared file system located in their on-premises Server, staff are reporting from home lack of resources as they used to share files when on site. For stakeholders the advantages include being able to divide up your content between frequently accessed or infrequently accessed storage classes, that saves some serious cash.

In the future Hodan School will have a hundred EC2 instances with each hosting a web application, Database Servers, Active Directory Server, Network Server and Backup Storage which Hundreds of thousands of people are accessing these servers on a regular basis that will producing HUGE amounts of data.

To solve that problem in different stages I begin with implementing an architecture of 2 Linux instances sharing files from different availability zones in the same VPC for this project. 

Below Diagram represents the complete stages of this project, when we are going to implement secure connection from on-premises to AWS cloud and staff are able to access their shared storage in either on-site or working from home, here is a the diagram. 

![Elastic File System](https://github.com/MoRoble/AWS-Network-Storage/blob/d84a35545eb15e44b372ab52b2c5fe8312f5810f/Hodan-EFS2.png)

Elastic File System is useful product in AWS which provides network file system that can be mounted within Linux instances and used multiple instances at once. It will allow us to store resources that will not be lost when instances are added or removed, and that provides significant benefits in terms of scaling as well as self-healing architecture.

I will be using CloudFormation to provision the instances, subnets, security groups and the VPC as part of one-click deployment, here's the link 


  *I will be using temporarily OneClick deployment since it requires paid storage* 
  
- `us-east-1` will be my region for this project  
- Once first templete is in `CREATE_COMPLETE` status, then the second for instance provisioning.

   - [One-Click VPC Deployment](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://hubeyda.s3.eu-west-2.amazonaws.com/HDN_EFS_VPC.yaml&stackName=HoDaN)
   - [One-Click Instances Deployment](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://hubeyda.s3.eu-west-2.amazonaws.com/HDN_EFS_Instances.yaml&stackName=HDN-EC2)

Once stack provision is complete, then I will implement file system by following these steps:  

Start with creating files system, go to EFS from services then create File System named `HD-EFS`, modify network settings using security group associated with `Hodan-VPC`.

Next connect `HD-EC2-A`, install `amazon-efs-utils` then make directory named `Hodan-Resources` under `/efs/Hodan-Resources`.

There are two ways of mounting file system to an instance:
- EFS Can be configured On Launch instance wizard.
- Update `fstab` file on EC2 instance

For this project I will be updating `fstab` file on both `HD-EC2-A & B` instances, to do that copy and modify this line of code and paste it in 2nd line of fstab file.

`file-sytem-id:/ /efs/Hodan-Resources efs _netdev,tls,iam 0 0`

now mount the directory to instance using this code

`sudo mount /efs/Hodan-Resources`

then move into `cd /efs/Hodan-Resources` folder to create text file named `hubeyda.txt` to check that this is in fact a network file system.

I am going to do the same steps on `HD-EC2-B`, once `Hodan-Resources` folder mounted then I will check `hubeyda.txt` file is available there.

![Proect success](https://github.com/MoRoble/AWS-Network-Storage/blob/main/Test-success.png)"Success!"

That proves this is shared network file system where any file added on one instance are visible to all other instances.

This project will be continued to expand connecting **Site-to-Site VPN** connection to make all those files visible to On-premises devices.


🦋*I hope that was informative til next time I would like to thank you* (⌐■_■)

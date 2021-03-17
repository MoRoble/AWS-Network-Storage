# AWS-Network-Storage

### Network Storage
##### Overview
I am pleased to submit this outline for migration of Elastic Files System at Hodan School. My proposal is based on the school required upgrade due to staff are working from home. The alternative is when staff are fully back on site to upgrade this plan to migrate to local on-premises server so that shared folder will be mounted to all devices in the school and all staff user profiles end to end.

#### Elastic File System

I will be using EFS as part of this project to upgrade Hodan School Network Storage to a way more flexible, elastic, durable and accesible from anywhere. Currently, they have shared file system located in their on-premises Server, staff are reporting from home lack of resources as they used to share files when on site.

To solve that problem in different stages I begin with implementing an architecture of 2 Linux instances sharing files from different availability zones in the same VPC for this project. 

Below Diagram represents the complete stages of this project, when we are going to implement secure connection from on-premises to AWS cloud and staff are able to access their shared storage in either on-site or working from home, here is a the diagram. 

![Elastic File System](https://github.com/MoRoble/AWS-Network-Storage/blob/d84a35545eb15e44b372ab52b2c5fe8312f5810f/Hodan-EFS2.png)

Elastic File System is useful product in AWS which provides network file system that can be mounted within Linux instances and used multiple instances at once. It will allow us to store resources that will not be lost when instances are added or removed, and that provides significant benefits in terms of scaling as well as self-healing architecture.

I will be using CloudFormation to provision the instances, subnets, security groups and the VPC as part of one-click deployment, here's the link 

Once stack provision is complete, then I will implement file system by following these steps:

# AWS-Network-Storage

### Network Storage
##### Overview
I am pleased to submit this outline for migration of Elastic Files System at Hodan School. My proposal is based on the school required upgrade due to staff are working from home. The alternative is when staff are fully back on site to upgrade this plan to be migrated to local on-premises server so that all devices in the school and all staff will be able to mount shared drive to their user profiles end to end.

#### Elastic File System

I will be using EFS as part of this project to upgrade Hodan School Network Storage to a way more flexible, elastic, durable and accesible from anywhere. Currently, they have shared file system located in their on-premises Server, staff are strugling to share their resources as they used to share when on site, due to staff working from home it demanded to have all that resources be accessible from anywhere. 

To begin with I have designed a diagram to illustrate the architecture of 2 Linux instances sharing files from different availability zones in the same VPC for this project. 

Later I want to expand this project to make all staff user profiles get their shared drive mounted to file server so that will be accessible to any device they roam around, here is a diagram. 

![Elastic File System](https://github.com/MoRoble/AWS-Network-Storage/blob/d84a35545eb15e44b372ab52b2c5fe8312f5810f/Hodan-EFS2.png)

Elastic File System is useful product in AWS which provides network file system that can be mounted within Linux instances and used multiple instances at once. It will allow us to store resources that will not be lost when instances are added or removed, and that provides significant benefits in terms of scaling as well as self-healing architecture.

# AWS-Network-Storage

### Network Storage
#### Elastic File System


Hodan School have requested to implement Network Storage for their staff to share resources and files. Currently, they have shared file located in their local Server, due to staff working from home it demanded to have all that resources be accessible from anywhere. 

To begin with I have designed a diagram to illustrate the architecture of 2 Linux instances sharing files from different availability zones in the same VPC for this project. 

Later I want to expand this project to make all staff user profiles get their shared drive mounted to file server so that will be accessible to any device they roam around, here is a diagram. 

![Elastic File System](https://github.com/MoRoble/AWS-Network-Storage/blob/d84a35545eb15e44b372ab52b2c5fe8312f5810f/Hodan-EFS2.png)

Elastic File System is useful product in AWS which provides network file system that can be mounted within Linux instances and used multiple instances at once. It will allow us to store resources that will not be lost when instances are added or removed, and that provides significant benefits in terms of scaling as well as self-healing architecture.

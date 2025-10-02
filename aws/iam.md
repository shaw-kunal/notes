Pending: 122, 123


# Day 124 || IAM Policies - IAM Customer Managed Policies 

We have seen , there are some limitation in aws managed policies
 -  Resource-specific Access Control
 -  No Customization
 -  Broad Permission
 -  Dependence on AWS
 -  Understanding Complexity

 ## Customer Managed Policies

 *Introduction:*
  - Created and managed by users
  - Tailored for specific needs
  - Attached to multiple IAM Entities
  - Manual Update Required
  - Enables Fine-grained Permission Control
  - Versioning and Rollback


 **Example**
 
 *Objective:* -  To configure IAM permission that the user "ec2mastermind" is authorized to managed (eg: start , stop and terminate) only two out of three aws instances
 *Policy User:* - Custom Policy
 *Entity:* - IAM user named EC2MasterMind
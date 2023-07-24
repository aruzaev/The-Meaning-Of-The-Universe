# [[EC2]]

EC2 (Elastic Compute Cloud) is an [[AWS]] service that amazon offers which allows you to rent out [[virtual machine]]s ([[EC2]]), store data on virtual drives ([[EBS]]), distribute load across machines ([[ELB]]), and scale services using an auto scaling group ([[ASG]])


## Create an EC2 Instance with EC2 User data for a website
---
.pem is for linux, mac, and windows 10 and above

.ppk is for lower than windows 10


[[EC2 Basics]]
[[EC2 Instances]]
[[Security Groups]]
[[SSH]]
[[EC2 Instances Purchasing Options]]

- EC2 Instance: [[AMI]] (OS) + Instance Size (CPU + RAM) + Storage + security groups + EC2 User Data
- Security Groups: Firewall attached to the [[EC2 Instances]]
- EC2 User Data: script launched at  the first start of an instance
- EC2 Instance Role: Link to iam roles
- Purchasing Options: [[EC2 On Demand]], [[EC2 Spot Instances]], [[EC2 Reserved Instances]], [[EC2 Reserved Instances]] (standard + convertible + scheduled), [[EC2 Dedicated Hosts]], [[EC2 Dedicated Instances]]


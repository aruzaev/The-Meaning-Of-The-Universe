# [[Security Groups]]

[[AWS]] [[EC2]]

Fundamental way to secure our AWS network. The groups control how traffic is allowed into or out of our EC2 Instances

They only contain allow rules

Security groups can reference by IP or by security group

## Deeper Dive
---
Security groups are acting as a firewall on EC2 instances

They regulate:
- Access to ports
- Authorized IP Ranges - IPv4 and v6
- Control inbound network (from outside to the instance)
- Control outbound network (from instance to the outside)

![[Security groups diagram.png]]

## Good to know
---
- Security Groups can be attached to multiple instances
- They are locked  down to a region or a [[VPC]] (virtual private cloud, another AWS service)
- Lives outside of the EC2 instance, the instance wont be able to see the blocked traffic at all
- Good idea to maintain one separate security group for [[SSH]] access
- **[[If application is not accessible or it has timed out, then its a security issue]]**
- If application gives a connection refused, then theres an issue with the actual application or it isnt launched
- All inbound traffic is blocked by default
- All outbound traffic is authorized by default

Good [[Ports]] To Know
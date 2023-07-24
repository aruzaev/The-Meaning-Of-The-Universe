# [[Tenancy]]

url: https://docs.aws.amazon.com/autoscaling/ec2/userguide/auto-scaling-dedicated-instances.html

Tenancy defines how [[EC2 Instances]] are distributed across physical hardware and affects pricing. There are three tenancy options available:

- Shared (`default`) — Multiple AWS accounts may share the same physical hardware.
- Dedicated Instance (`dedicated`) — Your instance runs on single-tenant hardware.
- Dedicated Host (`host`) — Your instance runs on a physical server with [[EC2]] instance capacity fully dedicated to your use, an isolated server with configurations that you can control.
# [[SSH]]

SSH allows you to control a remote machine with a command line 

You can either use SSH with Mac and Windows with a version 10 or higher

OR 

Use Putty for older version of windows 

[[EC2]] also allows to connect to [[EC2 Instances]] via [[EC2 Instance Connect]] which uses the browser and all OSes are supported

## How to connect to EC2 Instance with SSH
---
```
ssh -i bleh.pem ec2-user@54.90.134.174
```
Make sure the ssh key is in the same directory as your terminal

Do:
```
chmod 0400 bleh.pem
```
if connecting for the first time and you get an error saying "too open" or something
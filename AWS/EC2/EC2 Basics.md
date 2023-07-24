# [[EC2 Basics]]

to configure EC2, you need to take into account the following configurations:

- What operating system you would like to have as a virtual machine (Linux, Windows, or Mac OS)
- How much compute power and cores you'd like to have (CPU)
- How much RAM you'd like to have
- How much storage space you need (can be network attached storage (EBS and EFS) or hardware (EFS Instance store)
- Network card, the speed that you need and the public IP address of your application
- What firewall rules will be put in place
- The configuration when you first launch the application (Bootstrap script with EC2 User Data)


[[Bootstrapping]] means to run a list of commands on first startup

in the context of EC2, this could mean:

- installing updates
- installing software
- downloading common files from the internet
- anything else

Runs with the root user
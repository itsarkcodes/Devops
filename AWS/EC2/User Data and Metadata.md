# User Data
- You provide the command i.e Bash, Powershell, Batch Scripts
- limited to 16kb
- Eg. Installing a service on the instance which you can provide it in a script formet which will run on our ec2 instance

# Metadata
- Metadata is data about your EC2 Instance
- it can provide data like ami id, hostname, instance-id, instance-life cycle, etc
- Eg: http://169.254.169.254/latest/meta-data/local-ipv4
- The above example will give you the private ip of the instance 

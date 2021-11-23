# Jenkins-CICD
### Build Automation and CI/CD with Jenkins

Launch an Amazon ubuntu EC2 instance and choose an instance type.
Create a new Security Group,
- In Security group name enter WebServerSG or any preferred name of your choice and provide a description.

- Choose your VPC from the list, you can use the default VPC.

- On the Inbound tab, add the rules as follows:

- Click Add Rule, and then choose SSH from the Type list. Under Source, select Custom and in the text box enter <public IP address range that you decided on in step 1>/32 i.e 172.23.23.165/32.

- Click Add Rule, and then choose HTTP from the Type list.

- Click Add Rule, and then choose Custom TCP Rule from the Type list. Under Port Range enter 8080.

- Click Create. 

I will be running Jenkins as a Docker Container.

Lauch the ec2 instance with the new security group created.

SSH into the instance created.

Run;

`apt update`

install Docker;

`sudo apt install docker.io`
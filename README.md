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


Lauch the ec2 instance with the new security group created.

SSH into the instance created.

Run;

`apt update`

we be installing Jenkins as a Docker Container.

install Docker;

`sudo apt install docker.io`


Pull the official jenkins image and expose it on port 8080

```
docker run -p 8080:8080 -p 50000:50000 -d \
-v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

Running  `docker ps ` will show the jenkins containner running.

Access the jenkins UI from your instance public URL on port 8080.


print the initialisation password
```
cat
/var/snap/docker/common/var-lib-docker/volumes/jenkins_home/
_data/secrets/initialAdminPassword

```

### Configure plugin for maven
From Jenkins UI,
- go to manage plugins
- go to global tool configuration
- in the Maven section, click on 'Add maven'
- name your maven configuration as the latest maven  version e.g maven-3.8
- save


### Install NPM and NODE in Jenkins container

Enter container as root

`docker exec -u 0 -it <containerID> bash`

*NB: the flag -u 0 allows us to log into the container as a root user

To check with linux distro our container is running

`cat /etc/issue`

run these commands to update and install curl;

```
apt update

apt install curl

```

Run these commands to install Nodejs and npm

```

curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh

bash nodesource_setup.sh

apt install nodejs

apt install npm

```

check your nodejs and npm version

```
nodejs -v
npm -v

```

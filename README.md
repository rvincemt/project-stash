# Stash
Project: Stash is a personal project of mine which aims for an easy deployment of central log management server for log aggregation, security and event analysis. 

## Design:
The design for this is contained here:
TODO: Link to Diagram

### Design Notes:
* Separate remote central log server from Logstash + Elastic Search cluster and Kibana reporting. 

## Tools:
* Docker
* Docker Compose
* Docker containers:
  * Logstash
  * Elastic Search
  * Kibana
  * rsyslog



## Platforms Needed:
* 1 microinstance Ubuntu/Debian Server to contain the rsyslog (1 free AWS instance, anyone?)
* 1 instance for Logstash and Elasticsearch container to separate traffic. (2core,8gbRAM,50GB memory would suffice)
* 1 Instance for web facing apps such as Kibana, Wordpress. (Either separate it to save the computing resource from your Elastic Stack, or bundle it).

## Pre-requisites:

#### Ubuntu (18.04) Bionic and Debian Buster (9):
This block updates and upgrades the applications on your server.

```
sudo apt update
sudo apt-get upgrade
```

### Docker / Docker-Compose
#### Step by step for installing Docker and Docker Compose to all VMs/Instances on Ubuntu Bionic (18.04) OR Debian 9. :

>Re-update repository
```
sudo apt update
```
>Enable APT over HTTPS, CA-Certs, Curl, etc:
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
>Add Docker repo. NOTE: if you're running debian, change 'ubuntu' to 'debian'
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"  
```
>Reupdate repository after adding external repo:
```
sudo apt update
```
>Install Docker CE and Docker Compose tools:
```
sudo apt install docker-ce
sudo apt install docker-compose
```
>Update Docker-Compose to support latest docker version:
```
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```
>Re-enable executable permission for docker-compose.
```
sudo chmod +x /usr/local/bin/docker-compose
```

#### Full code, please change 'ubuntu' to 'debian' if you're running Debian:

```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"  
sudo apt update
sudo apt install docker-ce
sudo apt install docker-compose
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### Java:

#### Install Java on Logstash and Elasticstash Instances/VM on Ubuntu Bionic (18.04) and Debian Buster (9):

```
sudo add-apt-repository -y ppa:webupd8team/java
sudo apt update
sudo apt-get -y install oracle-java8-installer
```


### Optional: Add User 'dockerman' to the machines for easy management and eliminates the need for 'sudo' on docker management. 
```
sudo adduser dockerman
sudo usermod -aG docker ${USER} 
sudo usermod -aG docker dockerman
```

Once done, you should be able to log-out and log back in as 

After installing the pre-requisites for the machines, we're good to go! For each machine/instance/node, check out the READMEs on each folder.



# Credits:

* DigitalOcean Guides:
https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04
https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04

# Visit my blog!
https://www.rvmaitim.me

# Upcoming Smart Home Tools/Product Store:
https://homeio.studio





# Local CI/CD Environment

#### This compose file spins-up a local CI/CD environment on Ubuntu for testing purposes. <br>


### Prerequisites
Docker + Docker Compose Ubuntu 20.04

```shell
### Docker and docker compose prerequisites
sudo apt-get install curl gnupg ca-certificates lsb-release &&\

### Download the docker gpg file to Ubuntu
sudo mkdir -p /etc/apt/keyrings &&\
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg &&\

### Add Docker and docker compose support to the Ubuntu's packages list
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-pluginsudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-pluginlinux/ubuntu   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null &&\

sudo apt-get update &&\
 
### Install docker and docker compose on Ubuntu
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Sources: 
- https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-install-Docker-and-docker-compose-on-Ubuntu
- https://dev.to/ashiqursuperfly/jenkins-controller-agent-master-slave-setup-in-10-minutes-using-docker-2a78

Run Compose:
```shell
docker-compose -f docker-compose-cicd.yaml up -d
```

## Jenkins

## Sonarqube

#### Default Credentials ###
```shell
User: admin
Password: admin
```

## Troubleshooting
1. Not enough VM RAM set; Error reads:
```shell
[1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
```

#### Set VM MAX:
Fix (temp):
```shell
sysctl -w vm.max_map_count=262144
```
Fix (permanent):
```shell
echo "vm.max_map_count=262144" >> /etc/sysctl.conf &&\
sysctl --system
```





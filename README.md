# Elastic Stack (ELK) for GnosisVIP on Docker
This repository will allow you to run the latest version of the Elastic stack alongside Gnosis Execution and Consensus Clients with Docker and Docker Compose.

Based on the official Docker images from Elastic:
* [Elasticsearch](https://github.com/elastic/elasticsearch/tree/main/distribution/docker)
* [Logstash](https://github.com/elastic/logstash/tree/main/docker)
* [Kibana](https://github.com/elastic/kibana/tree/main/src/dev/build/tasks/os_packages/docker_generator)
* [Nethermind](https://github.com/NethermindEth/nethermind)
* [Lighthouse-HOPR](https://github.com/Gnosis-Builders/lighthouse-hopr)

---
## Requirements
### Host setup
#### Accessing Digital Ocean and updating packages
```console
ssh root@<IPV4 Address here>
sudo apt -y update && sudo apt -y upgrade
sudo apt dist-upgrade && sudo apt autoremove
sudo reboot
```
#### Setup Networking
```console
sudo apt install ufw 
sudo ufw default allow outgoing 
sudo ufw allow 30303 
sudo ufw allow 9000
```

#### Install Docker Compose
```console 
sudo apt install docker-compose
```
##### Clone this repository
```console
git clone <GITHUB_HTTP>
```
#### Generate JWT Secret
```console
openssl rand -hex 32 | tr -d "\n" > /home/$USER/gnosis-hopr/jwtsecret/jwt.hex
```
## Usage
### Bringing up the stack
Once the repository has been clones, start the stack's services locally using Docker Compose. This process will take 10-15 mins.
```console
$ docker-compose up -d
```
Give Kibana about a minute to initialize, then access the Kibana web UI by opening <http://localhost:5601> in a web
browser and use the following (default) credentials to log in:

* user: *elastic*
* password: *changeme*

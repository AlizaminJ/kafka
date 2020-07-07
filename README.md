# kafka crash course

# Requirements:
- Java installed Ubuntu VPS. For VPS, you may try <a href="https://aws.amazon.com/lightsail/">AWS Lightsail</a> or <a href="https://www.digitalocean.com/products/droplets/"> Droplets on Digital Ocean </a>

# Process:
- Connect to VPS via ssh
- Install java
```
sudo apt update && sudo apt -y upgrade
sudo apt -y install openjdk-11-jre-headless
```
- Install binary version kafka on https://kafka.apache.org/downloads: Get the installation link (it suggests the closest server, in my case "https://apache.uib.no/kafka/2.5.0/kafka_2.12-2.5.0.tgz", create and download the file into "Downloads" directory, and finally install it into a new "kafka" directory 
```
curl https://apache.uib.no/kafka/2.5.0/kafka_2.12-2.5.0.tgz -o Downloads/kafka.tgz
mkdir kafka
cd kafka
tar -xvzf ~/Downloads/kafka.tgz --strip 1
```

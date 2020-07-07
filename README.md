# kafka crash course

# Requirements:
- Java installed Ubuntu VPS. For VPS, you may try <a href="https://aws.amazon.com/lightsail/">AWS Lightsail</a> (which I use) or <a href="https://www.digitalocean.com/products/droplets/"> Droplets on Digital Ocean </a>
- Choose 4G RAM VPS not to encounter memory issues

# Process:
- Connect using your own SSH client to VPS with your .pem-file (you have to download it from Lightsail) after having created it:
```
ssh -i YOUR_PEM_FILE.pem YOUR_USER@VPS_IP_ADDESS
```

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
- Check the structure in kafka folder:
  - "bin" - all scripts
  - "config" - ".properties" files for configuration
  - "libs" - installed libraries
  - "logs" - logs files
  - "site-docs" - documentation
- After installation, if you try to start the server you will get error, because kafka needs to connect zookeeper:
```
bin/kafka-server-start.sh config/server.properties
```
- So start zookeper (default port localhost:2181), then start the server (default port localhost:9092) in a new terminal while zookeper is running:
```
bin/zookeeper-server-start.sh config/zookeeper.properties
```
- Kafka saves logs in "logs" folder but messages are stored in /tmp/kafka-logs (!) whcih are automatically created by kafka server. To check running brokers in kafka-logs:  
```
cat meta.properties
```



### Setup Network
1. Edit the network-script
```
vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
 ...
 onboot=yes
```
2. Restart network
```
systemctl restart network
```
3. Check IP address
```
ip addr
```

### configure yum
```
yum update
```

### Install SSH
1. install (default no need to install)
```
# yum -y install openssh-server openssh-clients
```
2. Start the service:
```
# chkconfig sshd on
# service sshd start
```
3. Make sure port 22 is opened:(first: yum install net-tools)
```
# netstat -tulpn | grep :22
```

### Install ActiveMQ
https://www.vultr.com/docs/how-to-install-apache-activemq-on-centos-7

1. Install 1.8.0 java jdk
```
sudo yum install -y java-1.8.0-openjdk
```
2. setup environment
```
echo "JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::")" | sudo tee -a /etc/profile
source /etc/profile
```
3. Install Apache ActiveMQ
```
wget https://archive.apache.org/dist/activemq/5.15.4/apache-activemq-5.15.4-bin.tar.gz
sudo tar -zxvf apache-activemq-5.15.4-bin.tar.gz -C /opt
sudo ln -s /opt/apache-activemq-5.15.4 /opt/activemq
```
4. Start ActiveMQ
```
cd /opt/activemq
sudo ./bin/activemq start
```
5. Add as service
```
sudo vi /usr/lib/systemd/system/activemq.service

[Unit]
Description=activemq message queue
After=network.target
[Service]
PIDFile=/opt/activemq/data/activemq.pid
ExecStart=/opt/activemq/bin/activemq start
ExecStop=/opt/activemq/bin/activemq stop
User=root
Group=root
[Install]
WantedBy=multi-user.target
```
Start service
```
sudo systemctl enable activemq.service
sudo systemctl start activemq.service
sudo systemctl stop activemq.service
```
6. Setup firewall(Optinal)
```
sudo firewall-cmd --zone=public --permanent --add-port=8161/tcp
sudo firewall-cmd --reload
```
7. Setup username/password
```
/opt/activemq/conf/jetty-real.properties
```

###

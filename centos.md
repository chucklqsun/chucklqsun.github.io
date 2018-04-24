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

### 

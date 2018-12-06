### How to setup server
https://help.ubuntu.com/lts/serverguide/openvpn.html.en#openvpn-pki-setup

### Generate tls-auth key
```
openvpn --genkey --secret /etc/openvpn/ta.key
```

### Setup server config for gateway through VPN
```
# ROUTE THE CLIENT'S INTERNET ACCESS THROUGH THIS SERVER:
push "redirect-gateway def1"
push "remote-gateway vpn_server_ip"
push "dhcp-option DNS 8.8.8.8"
```

### Setup packet forward
```
"net.ipv4.ip_forward=1" >> /etc/sysctl.conf && sysctl -p
```

### Setup firewall
sudo vim /etc/default/ufw
```
DEFAULT_FORWARD_POLICY="ACCEPT"
```

```
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

https://gist.github.com/barseghyanartur/e60fee8fb5c3f144eef33582f9723864

logstash
https://www.elastic.co/guide/en/logstash/current/installing-logstash.html

sysctl -w vm.max_map_count=262144

wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
sudo apt-get update && sudo apt-get install logstash


nginx reverse config

setup password first:
[root@ELK /]# mkdir -p /etc/nginx/passwd
[root@ELK /]# htpasswd -c -b /etc/nginx/passwd/kibana.passwd user 123455
```
server {
listen 0.0.0.0:5622;
server_name localhost;

# auth_basic "Kibana Auth";
# auth_basic_user_file /etc/nginx/passwd/kibana.passwd;

location / {
        proxy_pass http://localhost:5601;
#       proxy_redirect off;
}
}
```

https://pawelurbanek.com/elk-nginx-logs-setup

是logstash/conf/jvm.options
同样是修改里面的-Xmx 和-Xms的数值 => 512m

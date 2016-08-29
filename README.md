# binddns
Installing a BIND DNS service on CentOS 7
```
# yum install -y bind bind-utils
# systemctl enable named
# systemctl start named
# systemctl status named
# iptables -L
```
Package: bind  
Service: named  
Config: caching  
Port: 53  
```
# netstat -ltn
# dig www.google.com @127.0.0.1
```
Ensure there is a listening port 53 for ipv4 and ipv6  
```
# vim /etc/named.conf
```

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

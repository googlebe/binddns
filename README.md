# binddns Usage Instructions
Installing a BIND DNS service on CentOS 7 - Caching only
```
# yum install vim
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
Line 11+12: Change listen on to any and none, save and close  
```
listen-on port 53 { any; };
listen-on-v6 port 53 { none; };
```  
```
named-checkconf
```  
Troubleshoot any errors  
```
# systemctl restart named
# netstat -ltn
```  
Edit the configuration file again  
```
# vim /etc/named.conf
```
Edit line 17 to allow the string of machine on the ip range and local interfaces. In my previous example I used 192.168.56.0, save anc close  
```
allow query { localhost;  192.168.56.0/24;  localnets;  }
```
check the changes and restart the service. Resolve any errors if they occur  
```
# named-checkconf -v
# systemctl restart named
# systemctl status named
# netstat -ltn
# dig www.google.com
# dig www.pluralsight.com @127.0.0.1
```
Will redirect the name server to the localhost successfully  
```
# vim /etc/named.conf
```
Add the google forwarders below the details in configuration, around line 41  
```
forwarders  { 8.8.8.8;  8.8.4.4;  }
forward only;
```


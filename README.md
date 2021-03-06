docker-bind9 
================
This project build a bind9 domain name server configured to serve and accept updates for the root domain $BIND9_ROOTDOMAIN env variable.

Use the following ENV when running :
- "BIND9_IP" : public IP of the DNS
- "BIND9_ROOTDOMAIN" : the root domain (like : example.com)
- "BIND9_KEYNAME" : the name of the key
- "BIND9_KEY" : the key base64 encoded
- "BIND9_FORWARDERS" : the forwarders (like : 8.8.8.8;8.8.8.4;)
- "BIND9_IPV4ONLY" : set bind9 to support only IPV4


The port 53 must be exposed in tcp and udp to answer DNS requests. The server will accept any query, cache request, this is unsecure, be sure to know what you are doing.

Run with :
sudo docker run -e "BIND9_IP=10.10.12.23" -e "BIND9_ROOTDOMAIN=example.com" -e "BIND9_KEYNAME=secret" -e "BIND9_KEY=c2VjcmV0"  -e "BIND9_FORWARDERS=8.8.8.8;8.8.4.4;" -p 53:53/udp -p 53:53 digitallumberjack/docker-bind9:latest

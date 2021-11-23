```
GSSAPIAuthentication yes
GSSAPIDelegateCredentials yes

Host *
  ServerAliveInterval 60
Host jump_name_host
  hostname jump_name_host.domain
  User myuser


###########################
## List of remote nodes  ##
###########################
# Hosts with a common string in their hostnames

Host common_string_from_hosts*
  hostname %h.domain
  ProxyCommand ssh myuser@jump_name_host -W %h:%p
  User myuser


###########################
#     A particular host   #
###########################
Host remote_host
  #AAAA ports
  LocalForward 18080 remote_host:18080
  LocalForward 18081 remote_host:18081
  #JMX cassandra port
  LocalForward 7199 remote_host:7199
  #Kafka
  LocalForward 9000 remote_host:9000
  #Kibana
  LocalForward 5601 remote_host:5601
  #Unknown
  LocalForward 3010 remote_host:3010
  #Grafana
  LocalForward 3001 remote_host:3000
  #Prometheus
  LocalForward 9091 remote_host:9090

# By ip
Host 10.10.10.*
  ProxyCommand ssh frueda@remote_host -W %h:%p
  User otherusername

Host 11.11.11.*
  ProxyCommand ssh frueda@remote_host -W %h:%p
  User root
```


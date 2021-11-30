List rules:
```
firewall-cmd --list-services | grep -i cassandra
```
	
Create a file:
```
touch /etc/firewalld/services/cassandra.xml
```
Fill up with content:
```
	<?xml version="1.0" encoding="utf-8"?>
	<service>
	  <short>cassandra</short>
	  <description>cassandra service-input-tcp [7000,7199,9042]</description>
	  <port protocol="tcp" port="7000"/>`
	  <port protocol="tcp" port="7070"/>
	  <port protocol="tcp" port="7199"/>
	  <port protocol="tcp" port="9042"/>
	</service>
```
	
Add the new rule:
```
firewall-cmd --permanent --add-service=cassandra
```
> NOTE: if you are using RedHat you need to add to the file '/etc/firewalld/zones/public.xml' the following line (and after that launch the previous command): \<service name="cassandra"/>
		

Reload the rule in case of changes:
```
firewall-cmd --reload
```

Remove a firewall rule:
* if there are rich rules:
  ```
  $ firewall-cmd --list-all
  ```
	Then the command to remove them is like:
	 ```				
			firewall-cmd --permanent --remove-rich-rule='
			rule family="ipv4" \
			source address="192.168.1.11/27" \
			port protocol="tcp" port="XXXX" drop'
	 ```		
	where XXXX = 7000, 7001, 7199, 9042, 9160, 9142

* if there are no rich rules:
	 ```	
	firewall-cmd --remove-service=RULE_NAME --permanent 
	```

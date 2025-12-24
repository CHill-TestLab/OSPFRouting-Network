# OSPFRouting-Network
Packet Tracer display of OSPF routing within an enterprise

## Overview

This packet tracer file was designed by myself for a Tafe project; I thought it would be good to configure it with OSPF and actually get it working.

I already had the IP addressing scheme laid out so that was the first step.

|ID|VLAN|Subnet|Gateway|
|--|----|------|-------|
|5|Hypervisors|192.168.0.0|192.168.0.14|
|10|Servers|192.168.0.16|192.168.0.30|
|20|Marketing|192.168.0.32|192.168.0.62|
|30|HR|192.168.0.64|192.168.0.94|
|40|IT|192.168.0.96|192.168.0.126|
|50|C-Suite|192.168.0.128|192.168.0.158|
|60|Admin|192.168.0.60|192.168.0.190|
|70|Customer Service|192.168.0.192|192.168.0.222|
|80|Branch Office|192.168.0.224|192.168.0.254|
|90|DMZ|192.168.1.0|192.168.1.30|

## Switches

Configured VLAN 5-Hypervisors and VLAN 10-Servers with switchport trunking
<br>`switchport trunk allowed vlan ".No"`</br>

Configured all Access Switches with script:

<pre>
en
conf t
vlan "No."
name Customer Service
int "Port"
switchport mode trunk
switchport trunk allowed vlan "No."
int "Port"
switchport mode trunk
switchport trunk allowed vlan "No."
</pre>

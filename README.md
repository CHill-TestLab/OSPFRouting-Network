# OSPFRouting-Network
Packet Tracer display of OSPF routing within an enterprise

## Overview

This network topology was just created as a design concept during my networking studies. I thought it would be good to configure it with OSPF and make it a showcase piece.

I already had the IP addressing scheme laid, I just made some minor adjustments.

|ID|VLAN|Subnet|Gateway|CIDR|
|--|----|------|-------|----|
|5|Hypervisors|192.168.0.0|192.168.0.14|/28|
|10|Servers|192.168.0.16|192.168.0.30|/28|
|20|Marketing|192.168.0.32|192.168.0.62|/27|
|30|HR|192.168.0.64|192.168.0.94|/27|
|40|IT|192.168.0.96|192.168.0.126|/27|
|50|C-Suite|192.168.0.128|192.168.0.158|/27|
|60|Admin|192.168.0.60|192.168.0.190|/27|
|70|Customer Service|192.168.0.192|192.168.0.222|/27|
|80|Branch Office|192.168.0.224|192.168.0.254|/27|
|90|DMZ|192.168.1.0|192.168.1.30|/27|

## Switches

### Access Switches

Configured VLAN 5-Hypervisors and VLAN 10-Servers with switchport trunking
<br>`switchport trunk allowed vlan "ID"`</br>

Configured all Access Switches with script:

<pre>
en
conf t
vlan 'ID'
name Customer Service
int 'x/x/x'
switchport mode trunk
switchport trunk allowed vlan 'ID'
int 'x/x/x'
switchport mode trunk
switchport trunk allowed vlan 'ID'
</pre>

### Core Switches

Configured all connected interfaces with 
<pre>
int range g1/0/1-9
switchport mode trunk
switchport trunk allowed 5,10,20,30,40,50,60,70
</pre>

## Routers

Configured sub-interfaces on both ethernet ports to allow traffic from the VLANs.
<pre>
int g0/0/0.x
encapsulation x
ip address 192.168.0.x 255.255.255.x
</pre>

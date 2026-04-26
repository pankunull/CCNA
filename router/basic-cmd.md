# Basic Router Commands

## Show routing table

```
Router#show ip route
```

---

## Show IP interface brief

Quick view of interface status and IPs.

```
Router#show ip interface brief
```

---

## Show running configuration

Display current configuration.

```
Router#show running-config
```

---

## Show ARP table

View IP-to-MAC mappings.

```
Router#show ip arp
```

---

## Show MAC address table (L2 switch feature)

```
Router#show mac address-table
```

---

## Show interfaces

Detailed interface information.

```
Router#show interfaces
```

---

## Configure interface IP

Assign IP address to interface.

```
Router(config)#interface g0/0
Router(config-if)#ip address <ip> <subnet-mask>
Router(config-if)#no shutdown
```

---

## Default route

Configure gateway of last resort.

```
Router(config)#ip route 0.0.0.0 0.0.0.0 <next-hop>
```

---

## Static route

Manually define a route.

```
Router(config)#ip route <network> <mask> <next-hop>
```

---

## Floating static route

Backup route with higher AD.

```
Router(config)#ip route <network> <mask> <next-hop> <AD>
```

---

## Enable RIP

Basic RIP configuration.

```
Router(config)#router rip
Router(config-router)#version 2
Router(config-router)#network <network>
Router(config-router)#no auto-summary
```

---

## Enable OSPF

Basic single-area OSPF.

```
Router(config)#router ospf 1
Router(config-router)#network <network> <wildcard> area 0
```

---

## Enable EIGRP

Basic EIGRP configuration.

```
Router(config)#router eigrp 100
Router(config-router)#network <network>
Router(config-router)#no auto-summary
```

---

## Show routing protocols

View active routing processes.

```
Router#show ip protocols
```

---

## Show OSPF neighbors

```
Router#show ip ospf neighbor
```

---

## Show EIGRP neighbors

```
Router#show ip eigrp neighbors
```

---

## Show RIP database

```
Router#show ip rip database
```

---

## Save configuration

Write config to memory.

```
Router#write memory
```

or

```
Router#copy running-config startup-config
```

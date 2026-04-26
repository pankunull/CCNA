# Multilayer Switch (Layer 3 Switch) Commands

## Enable Layer 3 routing

Turns the switch into a router-capable device.

```
Switch(config)#ip routing
```

## Create VLAN (Layer 2 segmentation)

```
Switch(config)#vlan 10
Switch(config-vlan)#name USERS
```

## Configure SVI (Switch Virtual Interface)

Used for inter-VLAN routing.

```
Switch(config)#interface vlan 10
Switch(config-if)#ip address 192.168.10.1 255.255.255.0
Switch(config-if)#no shutdown
```

## Assign VLAN to access ports

```
Switch(config)#interface f0/1
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 10
```

## Enable inter-VLAN routing

Requires:
- VLANs created
- SVIs configured
- `ip routing` enabled

No extra command needed beyond SVIs.

## Configure routed port (Layer 3 interface)

Convert switch port into a router interface.

```
Switch(config)#interface g0/1
Switch(config-if)#no switchport
Switch(config-if)#ip address 10.0.0.1 255.255.255.0
Switch(config-if)#no shutdown
```

## Static routing

```
Switch(config)#ip route 0.0.0.0 0.0.0.0 <next-hop>
Switch(config)#ip route <network> <mask> <next-hop>
```

## Floating static route (backup path)

```
Switch(config)#ip route <network> <mask> <next-hop> <AD>
```

## Default gateway (Layer 2 mode only fallback)

Used only if `ip routing` is NOT enabled.

```
Switch(config)#ip default-gateway <ip>
```

## Show routing table

```
Switch#show ip route
```

## Show IP interfaces

```
Switch#show ip interface brief
```

## Show VLANs

```
Switch#show vlan brief
```

## Show SVIs

```
Switch#show ip interface brief | include Vlan
```

## Show routed interfaces

```
Switch#show ip route connected
```

## Show CEF (forwarding table)

```
Switch#show ip cef
```

## OSPF (Layer 3 switch routing)

```
Switch(config)#router ospf 1
Switch(config-router)#network 192.168.0.0 0.0.255.255 area 0
```

## EIGRP (Layer 3 switch routing)

```
Switch(config)#router eigrp 100
Switch(config-router)#network 192.168.0.0
Switch(config-router)#no auto-summary
```

## Verify routing protocols

```
Switch#show ip protocols
Switch#show ip ospf neighbor
Switch#show ip eigrp neighbors
```

## Inter-VLAN routing verification

```
Switch#ping <remote-vlan-ip>
Switch#traceroute <destination>
```

## Save configuration

```
Switch#write memory
```

or

```
Switch#copy running-config startup-config
```

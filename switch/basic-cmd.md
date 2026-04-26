# Basic Switch Commands

## Show MAC address table

View learned MAC addresses.

```
Switch#show mac address-table
```

## Show interface status

Quick port status overview.

```
Switch#show interfaces status
```

## Show VLANs

List VLANs and assigned ports.

```
Switch#show vlan brief
```

## Show trunk ports

View trunk interfaces.

```
Switch#show interfaces trunk
```

## Show spanning-tree

Display STP information.

```
Switch#show spanning-tree
```

## Configure access port

Assign port to VLAN.

```
Switch(config)#interface f0/1
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan <vlan-id>
```

## Configure trunk port

Enable trunking.

```
Switch(config)#interface g0/1
Switch(config-if)#switchport mode trunk
```

## Set trunk allowed VLANs

Restrict VLANs on trunk.

```
Switch(config-if)#switchport trunk allowed vlan <vlan-list>
```

## Create VLAN

Add a VLAN.

```
Switch(config)#vlan <vlan-id>
Switch(config-vlan)#name <name>
```

## Delete VLAN

Remove a VLAN.

```
Switch(config)#no vlan <vlan-id>
```

## Assign VLAN to multiple ports

```
Switch(config)#interface range f0/1-10
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan <vlan-id>
```

## Enable PortFast

Fast transition to forwarding (access ports only).

```
Switch(config-if)#spanning-tree portfast
```

## Enable BPDU Guard

Disable port if BPDU received.

```
Switch(config-if)#spanning-tree bpduguard enable
```

## Set STP mode

Choose spanning-tree mode.

```
Switch(config)#spanning-tree mode rapid-pvst
```

## Set root bridge

Force switch as root.

```
Switch(config)#spanning-tree vlan <vlan-id> priority 4096
```

## Set secondary root

Backup root bridge.

```
Switch(config)#spanning-tree vlan <vlan-id> priority 8192
```

## Show STP root

```
Switch#show spanning-tree root
```

## Enable port security

Limit MAC addresses on port.

```
Switch(config-if)#switchport port-security
Switch(config-if)#switchport port-security maximum <number>
Switch(config-if)#switchport port-security violation shutdown
Switch(config-if)#switchport port-security mac-address sticky
```

## Show port security

```
Switch#show port-security
```

## Shutdown / enable interface

```
Switch(config-if)#shutdown
Switch(config-if)#no shutdown
```

## Save configuration

```
Switch#write memory
```

or

```
Switch#copy running-config startup-config
```

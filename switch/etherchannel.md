# EtherChannel (Link Aggregation)

Combines multiple physical links into one logical link for redundancy and increased bandwidth.

## EtherChannel Concept

- Multiple interfaces → one Port-Channel
- STP treats it as a single link
- Load balancing is per-flow (not per-packet)

## LACP Configuration (Recommended)

### Create EtherChannel group

```
Switch(config)#interface range f0/1-3
Switch(config-if-range)#channel-group 1 mode active
```

- active = LACP enabled
- passive = listens for LACP
- on = static (no negotiation)

### Configure Port-Channel interface

```
Switch(config)#interface port-channel 1
Switch(config-if)#switchport mode trunk
```

(or access mode if needed)

## Static EtherChannel (no negotiation)

```
Switch(config)#interface range f0/1-3
Switch(config-if-range)#channel-group 1 mode on
```

## PAgP (Cisco proprietary)

```
Switch(config)#interface range f0/1-3
Switch(config-if-range)#channel-group 1 mode desirable
```

or

```
Switch(config-if-range)#channel-group 1 mode auto
```

## Verify EtherChannel

```
Switch#show etherchannel summary
Switch#show interfaces port-channel 1
```

## Load Balancing Check

```
Switch#show etherchannel load-balance
```

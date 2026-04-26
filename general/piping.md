# Piping (|) in Cisco IOS

The pipe (`|`) operator allows you to filter, search, and manipulate command output directly on the device. It is essential for working efficiently with large outputs like `show running-config`.

NOTE: filters are case-sensitive.

## Basic Syntax

```
<command> | <filter>
```

Example:
```
show running-config | include hostname
```

## Core Pipe Filters

## include

Displays only lines that match a given pattern.

```
show running-config | include interface
show ip interface brief | include up
show running-config | include hostname|interface|router
```

## exclude

Removes lines that match a pattern.

```
show running-config | exclude shutdown
show running-config | exclude !
```

## begin

Starts displaying output from the first match onward.
Useful for jumping directly into sections.

```
show running-config | begin interface GigabitEthernet0/0
```

## section

Displays entire sections that match a pattern.
More powerful than `include` because it returns full configuration blocks.

```
show running-config | section interface
show running-config | section router ospf
```

## count

Counts the number of matching lines.

```
show running-config | include interface | count
```

## Pattern Matching Tricks

## Match Exact Words (avoid partial matches)

(Note: Support depends on platform/version)

```
show running-config | include ^interface
```

## Chaining Pipes

You can combine multiple filters.

```
show running-config | include interface | exclude shutdown
```

## Limitations

- No full regex support (depends on IOS version)
- No AND logic directly (must chain pipes)
- Output is line-based (no true parsing)
- Case-sensitive matching


# Piping (|) in Cisco IOS

The pipe (`|`) operator allows you to filter, search, and manipulate command output directly on the device. It is essential for working efficiently with large outputs like `show running-config`.

---

## Basic Syntax

```
<command> | <filter>
```

Example:
```
show running-config | include hostname
```

---

## Core Pipe Filters

### 1. include

Displays only lines that match a given pattern.

```
show running-config | include interface
show ip interface brief | include up
```

Multiple patterns (OR logic):
```
show running-config | include hostname|interface|router
```

---

### 2. exclude

Removes lines that match a pattern.

```
show running-config | exclude shutdown
show running-config | exclude !
```

---

### 3. begin

Starts displaying output from the first match onward.

```
show running-config | begin interface GigabitEthernet0/0
```

Useful for jumping directly into sections.

---

### 4. section

Displays entire sections that match a pattern.

```
show running-config | section interface
show running-config | section router ospf
```

More powerful than `include` because it returns full configuration blocks.

---

### 5. count

Counts the number of matching lines.

```
show running-config | include interface | count
```

---

## Pattern Matching Tricks

### Multiple Matches (OR)

```
show running-config | include hostname|interface|router
```

---

### Match Exact Words (avoid partial matches)

IOS doesn’t support full regex anchors, but you can approximate:

```
show running-config | include ^interface
```

(Note: Support depends on platform/version)

---

### Case Sensitivity

Filters are case-sensitive.

```
include hostname   ← works
include Hostname   ← no match
```

---

## Chaining Pipes

You can combine multiple filters.

```
show running-config | include interface | exclude shutdown
```

Order matters (left → right processing).

---

## Useful Real-World Examples

### Find active interfaces only
```
show ip interface brief | include up
```

---

### Show all configured interfaces with details
```
show running-config | section interface
```

---

### Remove noise (comments and empty lines)
```
show running-config | exclude !
```

---

### Find specific IP addresses
```
show running-config | include 192.168.
```

---

### Count number of interfaces
```
show running-config | include ^interface | count
```

---

### Show only OSPF configuration
```
show running-config | section router ospf
```

---

### Find shutdown interfaces
```
show running-config | include shutdown
```

---

### Show lines after a match (manual context via begin)
```
show running-config | begin router bgp
```

---

## Limitations

- No full regex support (depends on IOS version)
- No AND logic directly (must chain pipes)
- Output is line-based (no true parsing)
- Case-sensitive matching

---

## Pro Tips

- Use `section` instead of `include` when you need full configs
- Use `exclude !` to clean output quickly
- Combine filters to simulate AND logic
- Always think in **line filtering**, not structured parsing
- Pipe is critical in exams when dealing with large configs

---

## Mental Model

- `include` → keep matching lines  
- `exclude` → remove matching lines  
- `begin` → jump to match  
- `section` → grab full block  
- `count` → quantify  

Think of pipe as a **post-processing filter for CLI output**.

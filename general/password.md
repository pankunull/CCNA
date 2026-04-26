# Password


### Encrypted global configuration password

**MD5**

```
Cisco(config)# enable secret 5 <password>
```

### Username and Password

```
username <user> secret 5 <password>
```

### Console port password



### Type 8 (recommended)

One-way SHA256 hash

```
Cisco(config)#enable algorithm-type sha256 secret <password>
Cisco(config)#username <user> algorithm-type sha256 secret <password>
```

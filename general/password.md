# Password

### Encrypted global configuration password

Configure MD5 encrypted password.

```
Cisco(config)# enable secret 5 <password>
```

### Username and Password

To enable local login authentication, configure the console line:

```
Cisco(config)#line console 0
Cisco(config)#username <user> secret <password>
Cisco(config-line)#login local
```

### Console port password

```
Cisco(config)# service password-encryption
Cisco(config)# line console 0
Cisco(config-line)# password <password>
Cisco(config-line)# login
```

### Type 8 (recommended)

One-way SHA256 hash.

```
Cisco(config)#enable algorithm-type sha256 secret <password>
Cisco(config)#username <user> algorithm-type sha256 secret <password>
```

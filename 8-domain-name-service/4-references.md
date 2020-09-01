# 4. References

### 4.1. Common Record Types

This section covers some of the most common DNS record types.

- _A_ record: This record maps an IP Address to a hostname.
```
www IN A 192.168.1.12
```

- _CNAME_ record: Used to create an alias to an existing _A_ record. You cannot create a _CNAME_ record pointing to another _CNAME_ record.
```
www IN CNAME www
```

- _MX_ record: Used to define where email should be sent to. Must point to an _A_ record, not a _CNAME_.
```
     IN MX 1 mail.example.com.
mail IN A    192.168.1.13
```

- _NS_ record: Used to define which servers serve copies of a zone. It must point to an _A_ record, not a _CNAME_. This is where Primary and Secondary servers are defined.
```
    IN NS ns.example.com.
    IN NS ns2.example.com.
ns  IN A  192.168.1.10
ns2 IN A  192.168.1.11
```

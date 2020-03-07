
# Transaction
- multi: when a command is failed to execute (e.g. syntax error) before exec, the transaction will be discard.
- exec: when a command in transaction is failed to execute, command(s) before fail will be executed. hence transaction is not atomic. use mset command for atomic uses.
- discard
- watch key1 key2 : watch a key before you multi command, if the key is updated by others, your exec command will fail
- unwatch: unwatch all the watched keys

# Other atomic commands
- GETSET
- SETNX
- MSETNX
- INCR


# Demo
### prepare data
```console
set ticket1status unused
get ticket1status
del ticket1tap
get ticket1tap
```

### monitor the keys
```console
watch ticket1status ticket1tap
```

### other client change the values
```console
set ticket1status voided
get ticket1status
#set ticket1tap tapin
#get ticket1tap
```

### start transaction
```console
multi
```

### use mset to ensure atomic execution
```console
mset ticket1status used ticket1tap tapin
exec
```

### check the values, expect ticket1status is unused, ticket1tap is nil
```console
get ticket1status
get ticket1tap
```

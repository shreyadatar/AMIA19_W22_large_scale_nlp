NB: To validate host connectivity, issue the folowing ad hoc ansible command to query against a list of all hosts in an inventory ini file under the group name classifier `[amia]`:
`ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory  -a "pwd" -c paramiko  --ask-pass amia`  

Each host in the group should be listed by row as

```
[amia]
<host name/ip 1> ansible_user=amia
...
<host name/ip n> ansible_user=amia
```



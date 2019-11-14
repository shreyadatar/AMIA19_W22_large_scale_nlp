NB: To validate host connectivity, issue the folowing ad hoc ansible command
to query against a list of all hosts in an inventory ini file under the group name classifier `[amia]` with each host in the group listed as `<host name/ip> ansible_user=amia`

`ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory  -a "pwd" -c paramiko  --ask-pass amia`

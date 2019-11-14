NB: To validate host connectivity, issue the folowing ad hoc ansible command
to query against a list of all hosts in inventory file under label `[amia]` with:
<host name/ip> ansible_user=amia

`ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory  -a "pwd" -c paramiko  --ask-pass amia`

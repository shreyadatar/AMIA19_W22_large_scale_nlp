# To validate host connectivity, issue the folowing ad hoc ansible command
# list all hosts in inventory file with `[amia]` label with list of:
# <host name/ip> ansible_user=amia

ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory  -a "pwd" -c paramiko  --ask-pass amia

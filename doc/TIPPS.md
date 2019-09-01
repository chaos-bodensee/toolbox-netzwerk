 Tipps:
==============

 Tags
--------

Man kann bei Ansible auch nur einzelen Tags ausführen. Zum Beispiel so:

```bash
ansible-playbook starswirl.yml --tags "strichliste"
```

 Ansible-Vault
---------------

Die sensibleren Daten wie die Zugangsdaten zu Switchen etc. sind mit einem [Ansible Vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html) verschlüsselt.
Das passende Passwort file dazu liegt in einem privaten git: ``https://gitea.see-base.de/toolbox/toolbox-ansible-vault.git``

### Ausführung:

Das Playbook kann wie folgt ausgeführt werden, sobald das git mit der ansible-vault file unter ../toolbox-ansible-vault/ geklont wurde.
```bash
ansible-playbook switche.yml --vault-password-file ../toolbox-ansible-vault/toolbox-ansible-vault.pwd
``` 

### Tricks:

SSh Jumphost for ansible:
```bash
ansible-playbook foo.yml --ssh-common-args="-o ProxyCommand='ssh -W [%h]:%p ansible@vh.tbbs.me'"
```



 Tipps:
==============

 Tags
--------

Man kann bei Ansible auch nur einzelen Tags ausführen. Zum Beispiel so:

```bash
ansible-playbook starswirl.yml --tags "strichliste"
```

 Switche
-----------
Die Switche werden per SSH gewartet. So muss deren Fingerprint auch in die ``~/.ssh/known_hosts`` gelangen.
Eine initiale SSH Verbindung kann man zB. mit folgenden extra parametern aufbauen:

```
ssh -c aes128-cbc,3des-cbc,aes192-cbc,aes256-cbc -oKexAlgorithms=+diffie-hellman-group1-sha1 toolbox@SWITCH_IP
```

 Telekom + IPv6
-------------
Um die IPv6 Route der Telekom zu unserem Router zu setzen, muss mit dhcpv6 das passende Prefix angefragt werden.
Damit wird dann die passende Route zu seinem Prefix gesetzt.

**Achtung:**, die Toolbox hat feste IP und IPv4 Adressen. Daher können die hier teilweise fest einkonfiguriert werden.
Für dynamische IP Adressen sieht das anders möglicherweise anders aus. Feste IP Adressen kosten aber idr. nur ein paar Euro mehr.

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

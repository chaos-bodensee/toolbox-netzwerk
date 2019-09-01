 Cisco Switche
========================
Die Cisco Switche werden mit Ansible Konfiguriert, gewartet und gemanaged.

**ALLES, WAS NICHT IM ANSIBLE IST,** wird gnadenlos überschrieben und gelöscht!

 $dinge im ansible ändern
--------------------------
Die jeweilige Switch-Configurationen befinden sich in dem ``host_vars`` Ordner im jeweiligen namen der Geräte!

Bitte **UNBEDINGT DORT** ändern und nicht in eigenen Rollen, Playbooks oder komplett ohne ansible.

**Deployed** wird das ganze über das ``switche.yml`` Playbook im root dieses git repos.

 technischer hintergrund
---------------------------
Die Cisco Geräte werden per SSH gewartet. So muss deren Fingerprint auch in die jeweilige lokale ``~/.ssh/known_hosts`` gelangen.
Eine initiale SSH Verbindung kann man zB. mit folgenden extra parametern aufbauen:

```
ssh -c aes128-cbc,3des-cbc,aes192-cbc,aes256-cbc -oKexAlgorithms=+diffie-hellman-group1-sha1 toolbox@SWITCH_IP
```

**ProTIPP:** Die IPs oder Hostnamen der Switche erfährt man aus dem ``ansible/hosts.ini`` Inventory.



 Das Netzwerk der Toolbox Bodensee e.V.
==============================

# Git hinweis

```bash
git clone https://github.com/ToolboxBodensee/toolbox-netzwerk.git
cd toolbox-netzwerk/
git submodule update --init --recursive
```

## Verkabelung:

```
[@] Internet
[T] Telekom DSL
[R] APU Router
[F] Freifunk Offloader
[Sⁿ] Switch
[Seⁿ] Server

 [@]
  |
 [T]-----[R]------[F]
          |        |
          '--[S¹]--' <-Netzwerkraum
             |||
      [S⁴]---'|'-------[S] <- 3D Druck [OG]      
 Bespr.raum   |'-------[S] <- Cyberlabor [OG]
              |'-------[S] <- Lounge [EG] [nicht aufgebaut]
              |
  [S³]-------[S²] <<-- Keller
 Rack1     Rack2
  |||         '---------------.
   |[Se¹: mrmeeseeks01]       |
   |[Se²: mrmeeseeks02]       |
   |[Se³: openstack]----------'
   |[Se⁴: kellernas]
 
```

## Geräte Hostnamen:

Die Interne Domain der Toolbox ist [tbbs.me.](https://tbbs.me.)<br/>
*Ist DNSSEC validiert und wird von L3D betreut*

```
[R] APU Router:
 + starswirl.tbbs.me.

[S¹] Switch im Netzwerkraum:
 + cheerilee.tbbs.me.

[S²] rechter Switch im Keller mit direkten Uplink:
 + princess-luna.tbbs.me.

[S³] linker Switch im Keller:
 + nightmare-moon.tbbs.me.

[S⁴] Besprechungsraum Switch (ruum42)
 + zecora.tbbs.me.

```

 VLANs:
--------------

**Status:** ''begonnen''

```
[1] Management
[2] Toolbox Clients
[3] Toolbox Servers
[4] Toolbox IOT [Kein Uplink]
[5] Guests [WAN Only]
[6] IPv6 ONLY
[7] Freifunk

[1] 100.100.0.0/20 [geplant]

[2] 172.23.16.0/20 

[3] 100.64.0.0/20 [geplant]

[4] 10.42.0.0/20 [geplant]

[5] 192.168.240.0/20 [geplant]

[6] fd00::/64 [geplant]

[7] 10.11.160.0/20 <- Remote from FFBSee
[7] fdef:1702:b5ee:42::/64 <- Remote from FFBSee

```

 Mithelfen
------------

**Mitarbeit** ist hier gerne gesehen. Für Zugänge zum Ansible Vault den [L3D](https://chaos.social/@l3d) oder Mart ansprechen.

**Zugang zu Geräten** gibt es *(mit ausnahme der Switche)* per SSH Key. *(ausschließlich ed25519 Keys)*<br/>
Hierfür deine SSH public Keys in ``/files/admin_ssh_keys/deinName.pub`` legen. *(Das ist in [diesem](https://gitea.see-base.de/toolbox/ssh-public-keys.git) Repo. Registrierung ist für jeden offen)*.<br/>
Außerdem musst du dein Name in die ``users`` variable des jeweiligen hosts packen. Für root Zugang dann auch in die ``admins`` variable.

**Wieso mitmachen?**<br/>
Die Toolbox ist ein Maker- und Hackerspace voller kreativer Menschen mit expertise in vielen Bereichen. Lass uns doch gegenseitig Wissen austauschen, anstatt dieses anderen vorzuenthalten.<br/>
**Wissen ist eine der Ressourcen, die mehr wird, wenn man sie mit anderen teilt!**<br/>
Die [Authoren](https://github.com/ToolboxBodensee/toolbox-netzwerk/graphs/contributors) dieses Playbook sind bestimmt gerne bereit dir das ganze ausführlich zu erklären, wenn du Sie freundlich darum bittest.


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

Verschlüsselte variabeln erstellen:
```bash
# ansible-vault encrypt_string 'encrypted_secret_string_value' -n string_name >> vars.yml
```

Verschlüsselte variable mit passwort-file erstellen:
```
# ansible-vault encrypt_string 'encrypted_secret_string_value' \
  -n string_name \
  --vault-password-file ../toolbox-ansible-vault/toolbox-ansible-vault.pwd >> vars.yml
```



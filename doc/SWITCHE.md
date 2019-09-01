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

 Neues Gerät ins Ansible aufnehmen?
-----------------------------------
Um ein neuen Switch ins ansible aufzunehmen müssen die folgenden Punkte befolgt werden:

Dabei muss die Firmware das Kürzel ``K9`` enthalten und SSH unterstützen!

 1. Switch auf Werkseinstellungen zurücksetzen:
```bash
# einige der Befehle könnten funktionieren....
write erase
del flash:vlan.dat
del flash:config.text
reload
```

 2. dem Switch eine Management IPv4 Adresse geben
```ios
! dies kann je nach switch anders sein. googeln hilft!
conf t
ip default-gateway 172.23.16.1
interface vlan 1
  ip address 172.23.31.XXX 255.255.240.0
  no shutdown
```
Vergess nicht die IP auch im inventory zu hinterlegen!

 3. Hostnamen setzen
```iso
conf t
hostname $hostname
ip domain-name tbbs.me
```
Vergess nicht den hostnamen im DNS und im Inventory zu hinterlegen sowie in den ``host_vars``!

 4. SSH auf dem Switch aktivieren
```ios
! dies kann je nach switch anders sein. googeln hilft!
! als erstes einen ssh key generieren
crypto key generate rsa
!... google for more details plz
!
line vty 0 4
  transport input ssh
  login local
  password 7
  end
write
```

5. deploy via ansible


 How to Firmware Upgrade
--------------------------
 1. Download Firmware ifrom WEB to flash:
```iso
copy http://172.23.X.Y/firmware-k9.bin flash:firmware-k9.bin
```

 2. Modify boot sequence
```ìos
show boot
!
dir flash:
!
conf t
  boot system flash:firmware-k9.bin
```

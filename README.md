 Das Netzwerk der Toolbox Bodensee e.V.
==============================

# Git hinweis

```bash
git clone https://github.com/ToolboxBodensee/toolbox-netzwerk.git
cd toolbox-netzwerk/
git submodule update --init --recursive
```
 Mithelfen
------------

**Mitarbeit** ist hier gerne gesehen. Für Zugänge zum Ansible Vault den [L3D](https://chaos.social/@l3d) oder Mart ansprechen.

**Zugang zu Geräten** gibt es *(mit ausnahme der Switche)* per SSH Key. *(teilweise ausschließlich ed25519 Keys)*<br/>

Hierfür deine SSH public Keys in ``/files/admin_ssh_keys/deinName@keybezeichnung_id.pub`` legen. *(Das ist in [diesem](https://gitea.see-base.de/toolbox/ssh-public-keys.git) Repo. Registrierung ist für jeden offen)*.<br/>

Außerdem musst du dein Name in die ``users`` und die ``accounts`` oder eventuell ``admin`` variable des jeweiligen hosts oder gruppe packen. Weitere Details dazu in den READMEs [hier](https://github.com/DO1JLR/role_sshd/blob/master/README.md), [dort](https://github.com/ffbsee/role-ssh_authorized_keys/blob/master/README.md) und auch [da drüben](https://gitea.see-base.de/toolbox/ssh-public-keys/src/branch/master/README.md).<br/>


Um das zB. für den Router life zu nehmen, kann man das Playbook mit dem Tag newuser so ausführen:
```bash
ansible-playbook gateway.yml --tags newuser
```

**Wieso mitmachen?**<br/>
Die Toolbox ist ein Maker- und Hackerspace voller kreativer Menschen mit expertise in vielen Bereichen. Lass uns doch gegenseitig Wissen austauschen, anstatt dieses anderen vorzuenthalten.<br/>
**Wissen ist eine der Ressourcen, die mehr wird, wenn man sie mit anderen teilt!**<br/>
Die [Authoren](https://github.com/ToolboxBodensee/toolbox-netzwerk/graphs/contributors) dieses Playbook sind bestimmt gerne bereit dir das ganze ausführlich zu erklären, wenn du Sie freundlich darum bittest.

 Weitere Hilfe:
==================
* [NETZWERK.md](https://github.com/ToolboxBodensee/toolbox-netzwerk/blob/master/NETZWERK.md)
* [TIPPS.md](https://github.com/ToolboxBodensee/toolbox-netzwerk/blob/master/TIPPS.md)



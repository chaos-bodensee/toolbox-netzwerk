 ZUGANG zu den Geräten
========================

Der Zugang zu den Debian basierten Geräten findet erstmal ausschließlich per SSH statt.
Hier werden keine Passwörter verwendet, sondern SSH Schlüssel.

Wenn du dich damit überhaupt nicht auskennst, findest du eine schlechte einführung dazu [auf YouTube](https://www.youtube.com/watch?v=to5jZgQWOMQ).

 ProTipp:
----------
Wir befinden uns im Zeitalter der CYBER-Konflikte und Quantencomputer. Daher setzen wir hier ausschließlich auf starke Kryptografie aus eliptischen ED25519 kurven. [ED25519 auf wikipedia](https://de.wikipedia.org/wiki/Curve25519).
Andere als weniger sicher und für quantencomputer angreifbarere algorythmen wie RSA werden strategisch standardmäßig ignoriert.

Um einen solchen ed25519 Key zu generieren, funktioniert folgender Unix Befehl:
```bash
ssh-keygen -t ed25519
```

 SSH Zugang bekommen
-----------------------
Die Zugänge zu SSH werden ausschließlich per ansible deployed.
Dies geschieht in der Regel mit den Rollen [role-sshd](https://github.com/chaos-bodensee/role_sshd.git) und  [role-ssh_authorized_keys](https://github.com/ffbsee/role-ssh_authorized_keys.git).

In den READMEs der Rollen gibt es auch jeweil Hinweise, wie die variablen dazu aussehen müssen.

Die SSH Keys selber werden in dem Git Repo  [ssh-public-keys](https://gitea.see-base.de/toolbox/ssh-public-keys/) gespeichert.
Diese können da per Pull Request von jedem erweitert werden, der sich die Zeit nimmt sich dort zu registrieren.

### Wo wird mein User konfiguriert

Wenn dein ed25519 SSH Key commited ist, kann dein User konfiguriert werden.

Das geschieht über die ``group_vars`` oder ``host_vars``.

Eine ganz brauchbare Konfiguration ist in der ``group_vars/all.yml`` hinterlegt, die für alle nodes gilt.
Diese wird von jeder spezifischeren Regel überschrieben. Aber wenn nichts definiert ist, passt das so erstmal.


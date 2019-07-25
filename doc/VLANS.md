 VLANs in dem Toolbox Netz
======================00

Wie es in [doc/NETZWERK.md](https://github.com/ToolboxBodensee/toolbox-netzwerk/blob/master/doc/NETZWERK.md) schon zu sehen ist, gibt es hier mehrere Netze.

Jedes dieser Netze haben ein eigenes VLAN.

 SWITCHE
---------

Die Switche **im Ansible** können mit VLANs umgehen und werden über die jeweiligen ``host_vars`` der Switche konfiguriert.

**Protipp:**<br/>
Dies geschieht über die Rollen die mit ``"cisco"`` im Namen anfangen.

 ROUTER
----------

Der Router kann auch VLANs.

Die Netzwerk Konfiguration findet über Ansible statt. Bitte in den jeweiligen Interfaces nachschauen!

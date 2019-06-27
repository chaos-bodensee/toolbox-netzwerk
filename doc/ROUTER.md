 Toolbox ROUTER
==================

Der Hostname des Routers lautet ``starswirl.tbbs.me``. Das ist für die configuration gut zu wissen :-P

 Telekom + IPv6
-------------
Um die IPv6 Route der Telekom zu unserem Router zu setzen, muss mit dhcpv6 das passende Prefix angefragt werden.
Damit wird dann die passende Route zu seinem Prefix gesetzt.

**Achtung:**, die Toolbox hat feste IP und IPv4 Adressen. Daher können diese hier teilweise fest einkonfiguriert werden.
Für dynamische IP Adressen sieht das möglicherweise anders aus. Feste IP Adressen kosten aber idr. nur ein paar Euro mehr.

**Achtung:**
Momentan ist das IPv6 noch etwas buggy. L3D, Max oder Alex sagen gerne, wieso!


**ACHTUNG**: Irgendwie ist das alles kaputt.

Sollte man mal reparieren.

 geheime variablen
----------------------
Für manche Dinge wird ein ansible-vault eingesetzt.

Infos dazu in ``doc/TIPS.md``

<!-- # ansible-playbook gateway.yml --vault-password-file ../toolbox-ansible-vault/toolbox-ansible-vault.pwd -->

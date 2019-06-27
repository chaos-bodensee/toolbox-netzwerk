 Das Netzwerk der Toolbox Bodensee e.V.
==============================

# Git Hinweis

**Achtung**, dieses git repository enthält submodule. Diese können wie folgt runtergeladen werden:

```bash
# clone the git inclusive submodules
git clone --recursive https://github.com/ToolboxBodensee/toolbox-netzwerk.git

cd toolbox-netzwerk/
# clone and pull the submodules
git submodule update --init --recursive
```

## Protipp:
Der Befehl  `git status`` ist immer gut um eine Übersicht zu bekommen, was in dem git momentan so los ist.<br/>
Wenn du keine Erfahrungen mit git hast ist im Zweifelsfall ein neu clonen mit submodulen die richtige Wahl.


 Mithelfen
------------

**Mitarbeit** ist hier gerne gesehen. Bei Fragen gerne einfach ein Issue öffnen oder Menschen wie [L3D](https://chaos.social/@l3d), [Alex](https://github.com/Devil0000) oder [Max](https://github.com/maxbachmann) ansprechen.

Wie du Zugänge bekommst, erfährst du in [ZUGANG.md](https://github.com/ToolboxBodensee/toolbox-netzwerk/blob/master/doc/ZUGANG.md)

 Netzwerk Setup
------------------
Wir haben einen Großteil des Netzwerkes auch per ansible deployed und damit für jeden einsehbar und anpassbar gemacht.
Eine grundlegende Übersicht dazu gibt es in der [NETZWERK.md](https://github.com/ToolboxBodensee/toolbox-netzwerk/blob/master/doc/NETZWERK.md).

 Doku
------
Für nützliche Hinweise gibt es das ``doc/`` Directory.

**Schau da rein!** 

 Weitere Infos
----------------

* [Ansible-Crashkurs](https://media.ccc.de/v/gpn16-7574-ansible_crashkurs)

 Error Handling
-------------------------
Hinweise zu Fehlern der laufenden Services (zB. Strichlistenzertifikat ist abgelaufen) ausschließlich per Github Issue!)
Am besten direkt mit Fixenden Pull-Request.

 Das Netzwerk der Toolbox Bodensee e.V.
==============================

# Git

```bash
git clone https://gitea.see-base.de/toolbox/netzwerk.git
cd netzwerk/
git submodule update --init --recursive
```

Zum clonen der Submodule benötigst du einen SSH Schlüssel, der in deinem Profil eingetragen ist!
Einen bestimmten SSH Key kannst du so angeben:
```bash
GIT_SSH_COMMAND="ssh -i ~/.ssh/privater_ssh_key" git submodule update --init --recursive
```
**ACHTUNG:**
Einige Submodule sensible Daten wie die PPPOE Einwahldaten zur Telekom, Klartextpasswörter zu Cisco Geräten oder interne MAC Adressen von Geräten.
Daher sind nicht einige essentielle Submodules nicht öffentlich einsehbar. Für einen Zugang muss man sich auf [gitea.see-base.de](https://gitea.see-base.de/) registrieren und in die toolbox Gruppe dort aufgenommen werden. Dies können u.a. [L3D](mailto:ansible-access-to-gitea-toolbox@l3d.yt) und [Mart](mailto:martin.hellebrand@toolbox-bodensee.de) dir geben. Melde dich dafür bei denen im Slack, per [IRC](https://webirc.hackint.org/#irc://irc.hackint.org/#ffbsee) oder per E-Mail. *(GPG Keys sind vorhanden).*

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
      [S⁴]---'|'-------[S] <- 3D Druck       
 Bespr.raum   |'-------[S] <- Cyberlabor
              |'-------[S] <- Lounge
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

Die Interne Domain der Toolbox ist [tbbs.me.](https://tbbs.me.)
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
## VLANs:

**Status:** ''begonnen''

```
[1] Management
[2] Toolbox Clients
[3] Toolbox Servers
[4] Toolbox IOT [Kein Uplink]
[5] Guests
[6] IPv6 ONLY
[7] Freifunk
[8] Manual VMs (KVM,vbox,qemu,...)
[9] Openstack VMs

[1] 100.100.0.0/20 [geplant]
[1] fdff::/64 [geplant]

[2] 172.23.16.0/20 
[2] fdb0::/64 [geplant]

[3] 100.64.0.0/20 [geplant]
[3] fd50::/64 [geplant]

[4] 10.42.0.0/20 [geplant]
[4] fdee::/64 [geplant]

[5] 192.168.240.0/20 [geplant]
[5] fdef::/64 [geplant]

[6] fd00::/64 [geplant]

[7] 10.11.160.0/20 <- Remote from FFBSee
[7] fdef:1702:b5ee:42::/64 <- Remote from FFBSee

[8] 172.28.240.0/22 [geplant]

[9] 172.29.240.0/22 [geplant]


```

 Tipps:
--------

Man kann bei Ansible auch nur einzelen Tags ausführen. Zum Beispiel so:

```bash
ansible-playbook starswirl.yml --tags "strichliste"
```


 Toolbox Bodensee Netzwerk
=========================

## grobe Verkabelung:

*Die Verbindung von den wichtigsten Geräten!*

```
[@] Internet
[T] Telekom DSL
[R] Gateway
[A] APU
[F] Freifunk Offloader
[Sⁿ] Switch
[Seⁿ] Server

 [@]
  |
 [T]----[R]   [A]       [F]
         |               |
         '-----'===[S¹]--' <-Netzwerkraum
                   |||
            [S⁴]---'|'-------[S] <- 3D Druck [OG]      
       Bespr.raum   |'-------[S] <- Cyberlabor [OG]
                    |'-------[S] <- Lounge [EG] [nicht aufgebaut]
                    |
        [S³]-------[S²] <<-- Keller
       Rack1     Rack2
        |||        |||
       [Srv¹]    [Srv²]
 ```

## Geräte Hostnamen:

Die Interne Domain der Toolbox ist [tbbs.me.](https://tbbs.me.)<br/>
*Ist DNSSEC validiert und wird von L3D betreut*

### wichtige Teile des Netzes:

```
[R] Gateway
 + Unify Gateway:
   * PPPoE 
   * Routing
   
[A] APU2 ``dhcp.tbbs.me``
   * DHCP
   * DNS
   * ... 

[S¹] Switch im Netzwerkraum:
 + cheerilee.tbbs.me.

[S²] rechter Switch im Keller mit direkten Uplink:
 + princess-luna.tbbs.me.

[S³] linker Switch im Keller:
 + nightmare-moon.tbbs.me.

[S⁴] Besprechungsraum Switch (ruum42)

[Srv¹] Server im linken Rack im Keller
 + HIER in der Datei nicht weiter Dokumentiert

[Srv²] Server im rechten Rack im Keller
 + HIER in der Datei nicht weiter Dokumentiert
```


 Switche
----
S¹ bis S³ sind cisco switche und per ansible administriert. S⁴ ist ein passiver Switch. Dumm - aber leise.

 Static IPs
--------------
Static IPs are currently *(June 2019)* managed in the ``group_vars/router.yml`` file.

We currently only use the ``172.23.16.0/20`` subnet for all devices. THIS WILL CHANGE SOON.
There we dont give random IPs from the ``172.23.31/24`` range to clients in the network. Use this are for static dhcp leases.`

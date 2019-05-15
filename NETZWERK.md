 Toolbox Bodensee Netzwerk
=========================

## grobe Verkabelung:

*Die Verbindung von den wichtigsten Geräten!*

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
  |||        |||
 [Srv¹]    [Srv²]
 
```

## Geräte Hostnamen:

Die Interne Domain der Toolbox ist [tbbs.me.](https://tbbs.me.)<br/>
*Ist DNSSEC validiert und wird von L3D betreut*

### wichtige Teile des Netzes:

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

[Srv¹] Server im linken Rack im Keller
 + bisher nicht Dokumentiert

[Srv²] Server im rechten Rack im Keller
 + bisher nicht Dokumentiert
```

### Weitere von ansible betreute Geräte:

* Gruppe Motion:
  * cluster.tbbs.me
    * bietet temporären Filestorage für motion
  * webcam6.tbbs.me
    * Raspi mit motion installiert




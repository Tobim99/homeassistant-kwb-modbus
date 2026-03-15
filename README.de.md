# KWB Modbus for Home Assistant

[English](README.md) | [Deutsch](README.de.md)

Custom Integration zur Anbindung von KWB-Heizungen per Modbus TCP in Home Assistant.

## Funktionen

- Config Flow (UI-Setup in Home Assistant, keine YAML-Konfiguration notwendig)
- Entitäten für `sensor`, `select` und `button`
- Automatisch berechnete Pelletverbrauch-Sensoren für `Tag`, `Woche`, `Monat` und `Jahr` (aus dem Gesamtzähler)
- Automatische Erkennung aktiver Instanzen für Zusatzmodule (z. B. Heizkreise, Puffer)
- Frei benennbare Instanzen (z. B. `HC 1.1` -> `Wohnzimmer`)
- Expertenmodus für zusätzliche, standardmäßig deaktivierte Steuer-Selects
- Button `Re-run Sensor Discovery` zum erneuten Erkennen von Sensoren

## Unterstützte Heizgeräte

| Heizgerät | Getestet |
| --- | --- |
| KWB EasyFire | ✓ |
| KWB MultiFire | X |
| KWB PelletFire+ | X |
| KWB CombiFire | X |
| KWB CF 2 | X |
| KWB CF 1.5 | X |
| KWB CF 1 | X |

## Unterstützte Zusatzmodule

| Zusatzmodul | Getestet |
| --- | --- |
| Pufferspeicher | ✓ |
| Solar | X |
| Heizkreise | ✓ |
| Warmwasserbereitung (DHWC) | X |
| Zirkulation | X |
| Sekundärwärmequellen | X |
| Wärmemengenzähler | X |
| Kessel Master-Slave | X |
| WMM Autonom | X |

## Getestet mit

- Anlagen-/Firmware-Version: `22.4.0+`
- Legende: `✓` = getestet, `X` = nicht getestet

## Voraussetzungen

- Home Assistant mit installiertem HACS
- KWB-Controller mit aktiviertem Modbus TCP
- Netzwerkverbindung von Home Assistant zur KWB-Anlage
- Standard-Port: `502`

## Installation über HACS

1. HACS öffnen.
2. Zu `Integrationen` gehen.
3. `Benutzerdefinierte Repositories` öffnen.
4. Repository-URL eintragen: `https://github.com/Tobim99/homeassistant-kwb-modbus`
5. Kategorie `Integration` wählen.
6. Integration installieren.
7. Home Assistant neu starten.

## Manuelle Installation

1. Ordner `custom_components/kwb_modbus` in dein Home-Assistant-Konfigurationsverzeichnis kopieren.
2. Home Assistant neu starten.

## Einrichtung

1. In Home Assistant zu `Einstellungen -> Geräte & Dienste -> Integration hinzufügen`.
2. `KWB Modbus` auswählen.
3. Verbindung eintragen: Host (IP/Hostname), Port (Standard `502`) und Abfrageintervall (Sekunden).
4. Heizgerät auswählen.
5. Installierte Zusatzmodule auswählen.
6. Automatisch erkannte Instanzen prüfen und ggf. anpassen.
7. Optional eigene Instanznamen vergeben.

## Re-Konfiguration

Verbindungsdaten können später über die Integration (`...` Menü -> `Neu konfigurieren`) angepasst werden.

## Troubleshooting

- Fehler `cannot_connect`:
  Prüfe IP/Hostname, Port, Firewall und ob Modbus TCP an der Anlage aktiv ist.
- Keine oder unplausible Werte:
  Prüfe, ob das richtige Heizgerät und die passenden Zusatzmodule gewählt wurden.
- Fehlende Entitäten bei Zusatzmodulen:
  Nutze den Button `Re-run Sensor Discovery`.
- Schreibbare Optionen nicht sichtbar:
  Prüfe, ob `Expertenmodus` bei der Einrichtung aktiviert wurde.

## Debug-Logging aktivieren

```yaml
logger:
  default: info
  logs:
    custom_components.kwb_modbus: debug
```

## Bekannte Einschränkungen

- Es wird Modbus TCP verwendet (kein serielles Modbus RTU).
- Je nach KWB-Firmware und Anlagenkonfiguration können Register/Entitäten variieren. Bitte melde Abweichungen mit Firmware-Version, Gerätetyp und betroffenen Modulen als Issue: https://github.com/Tobim99/homeassistant-kwb-modbus/issues

## Support und Issues

- Issue Tracker: https://github.com/Tobim99/homeassistant-kwb-modbus/issues

Bitte bei Bugs immer angeben:

- Home-Assistant-Version
- Integrationsversion
- KWB-Gerätemodell
- Relevante Log-Ausgaben (`debug`)
- Kurze Reproduktionsschritte

## Hinweis

Dieses Projekt ist eine Community-Custom-Integration und nicht offiziell von KWB oder Home Assistant.

Die Nutzung erfolgt auf eigene Verantwortung und eigenes Risiko. Es wird keine Gewähr für Funktion, Verfügbarkeit, Kompatibilität oder Eignung für einen bestimmten Zweck übernommen. Der Autor übernimmt keine Haftung für direkte oder indirekte Schäden, Folgeschäden, Datenverlust oder Fehlfunktionen an Anlage, Hardware oder Software, die durch Installation, Konfiguration oder Nutzung dieser Integration entstehen.

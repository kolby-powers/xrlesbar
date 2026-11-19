# XRlesbar – E-Rechnung Viewer

XRlesbar macht XRechnungen lesbar: Das Tool prüft eine XRechnung (UBL oder CII) mit dem offiziellen KoSIT-Validator und zeigt sie als sauber druckbares PDF an. Es läuft komplett lokal und offline – Rechnungsdaten verlassen den Rechner nicht.

> **Status:** in Entwicklung, noch keine Version veröffentlicht.

## Funktionen

- XRechnung (XML, UBL oder CII) öffnen
- Prüfung gegen die XRechnung-Regeln mit verständlichem Ergebnis (gültig / Warnungen / Fehler)
- Darstellung mit den offiziellen KoSIT-Stylesheets als PDF
- PDF speichern und drucken
- automatische Update-Prüfung

## Voraussetzungen

- Windows, macOS oder Linux
- Java 17 oder neuer, z. B. kostenlos von [Adoptium (Eclipse Temurin)](https://adoptium.net/temurin/releases/?version=21)

## Download

Die aktuelle Version gibt es unter [Releases](https://github.com/kolby-powers/xrlesbar/releases).

## Fehler melden

Probleme und Wünsche bitte als [Issue](https://github.com/kolby-powers/xrlesbar/issues) melden. Bitte keine echten Rechnungen mit personenbezogenen Daten hochladen.

## Hinweise

XRlesbar nutzt Komponenten der Koordinierungsstelle für IT-Standards (KoSIT) sowie weitere Open-Source-Bibliotheken. Die Lizenzhinweise liegen jedem Release bei (`THIRD-PARTY-NOTICES`). XRlesbar ist kein offizielles Produkt der KoSIT.

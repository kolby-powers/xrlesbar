# XRlesbar – E-Rechnung Viewer

XRlesbar macht E-Rechnungen lesbar: Es prüft XRechnungen und ZUGFeRD-/Factur-X-Rechnungen mit den offiziellen Prüfregeln und zeigt sie als sauber druckbares PDF an – so, wie die Koordinierungsstelle für IT-Standards (KoSIT) die Darstellung vorgibt.

> **Status:** erste öffentliche Version 0.5. Solange die Versionsnummer mit 0 beginnt, ist XRlesbar noch in Entwicklung. **[Zum Download](#download)**

## Lokal und offline

XRlesbar ist ein Programm für den eigenen Rechner, kein Online-Dienst.

- **Rechnungen verlassen den Rechner nicht.** Öffnen, Prüfen und Umwandeln passiert vollständig lokal. Es gibt keinen Upload, kein Konto und keine Cloud.
- **Alles, was zum Prüfen gebraucht wird, steckt im Programm:** die Prüfregeln von KoSIT und FeRD, die Darstellungsvorlagen und die Schriften. XRlesbar lädt beim Prüfen nichts nach und funktioniert ohne Internetverbindung.
- **Präparierte Dateien kommen nicht durch:** Rechnungen, die externe Dateien oder Internetadressen nachladen wollen (z. B. über eine DOCTYPE-Angabe), werden abgelehnt.
- **Einzige Verbindung ins Netz: die Suche nach Updates – und nur, wenn Sie zustimmen.** Die Oberfläche fragt vorher, ob sie bei GitHub nach einer neuen Version suchen darf; auf Wunsch merkt sie sich die Antwort. Dabei geht eine Anfrage an GitHub, die Ihre IP-Adresse enthält, aber keine Rechnungsdaten. Eine neue Version wird nur installiert, wenn Sie das jeweils bestätigen. Die Kommandozeile sucht nie nach Updates.

## Funktionen

- **XRechnung** im Format UBL oder CII öffnen
- **ZUGFeRD- und Factur-X-PDFs** öffnen (ab ZUGFeRD 2.0); die eingebettete Rechnung wird herausgezogen und kann auch einzeln gespeichert werden
- **Prüfung** mit verständlichem Ergebnis: gültig, gültig mit Warnungen, ungültig oder nicht prüfbar (z. B. ältere XRechnung-Version)
  - XRechnung 3.0 mit dem KoSIT-Validator und der offiziellen KoSIT-Konfiguration
  - ZUGFeRD-Profile MINIMUM, BASIC WL, BASIC, EN 16931 und EXTENDED mit den offiziellen Prüfregeln von FeRD
- **Darstellung als PDF** mit den offiziellen KoSIT-Stylesheets; ungültige Rechnungen bekommen einen deutlichen Warnhinweis auf der ersten Seite
- **Oberfläche** mit Ampel, Meldungsliste und Vorschau; Datei öffnen oder ins Fenster ziehen, PDF speichern, drucken oder im PDF-Viewer öffnen, bei ZUGFeRD auch das Original-PDF ansehen
- Oberfläche und PDF-Beschriftungen auf **Englisch oder Deutsch**
- **Updates** nur nach Zustimmung; jede neue Version wird einzeln bestätigt, per Prüfsumme kontrolliert und eingesetzt

**Grenzen:** ZUGFeRD 1.0 wird nicht unterstützt. Manche Rechnungen im ZUGFeRD-Profil EXTENDED nutzen Angaben, die die offizielle KoSIT-Darstellung nicht abbilden kann (z. B. mehrere Fälligkeitsdaten); sie werden trotzdem geprüft und als Original-PDF gezeigt. In der Vorschau fehlen bei manchen Fenstergrößen einzelne dünne Rahmenlinien; das erzeugte PDF ist vollständig.

## Kommandozeile

```
java -jar xrlesbar.jar rechnung.xml -o rechnung.pdf
java -jar xrlesbar.jar rechnung.pdf -o rechnung-kosit.pdf --lang de
java -jar xrlesbar.jar rechnung.xml --validate-only
java -jar xrlesbar.jar rechnung.pdf --extract-xml -o rechnung.xml
```

Ausgaben der Kommandozeile sind englisch. Exit-Codes: 0 gültig (auch mit Warnungen), 1 Datei nicht verarbeitbar, 2 Aufruf fehlerhaft, 3 Java zu alt, 4 Rechnung ungültig oder nicht prüfbar (das PDF wird trotzdem geschrieben, mit Warnbalken).

## Voraussetzungen

- Windows, macOS oder Linux
- Java 17 oder neuer, z. B. kostenlos von [Adoptium (Eclipse Temurin)](https://adoptium.net/temurin/releases/?version=21)

## Download

- **[xrlesbar.zip](https://github.com/kolby-powers/xrlesbar/releases/latest/download/xrlesbar.zip)** – empfohlen: Programm mit Start-Skripten, die fehlendes Java erkennen und den Download anbieten
- [xrlesbar.jar](https://github.com/kolby-powers/xrlesbar/releases/latest/download/xrlesbar.jar) – nur das Programm
- Prüfsummen (`.sha256`), Lizenzhinweise und ältere Versionen: [Releases](https://github.com/kolby-powers/xrlesbar/releases)

**Starten:** ZIP in einen Ordner entpacken, in dem Sie schreiben dürfen (z. B. Dokumente – nicht „Programme“, sonst kann sich XRlesbar nicht selbst aktualisieren). Dann:

- **Windows:** Doppelklick auf `xrlesbar.jar` oder `Start.bat`
- **macOS:** Doppelklick auf `xrlesbar.jar` oder `Start.command`. Beim ersten Mal meldet macOS „nicht verifizierter Entwickler“: Rechtsklick auf die Datei → „Öffnen“ → „Öffnen“.
- **Linux:** `./start.sh` oder `java -jar xrlesbar.jar`

## Fehler melden

Probleme und Wünsche bitte als [Issue](https://github.com/kolby-powers/xrlesbar/issues) melden. **Bitte keine echten Rechnungen mit personenbezogenen Daten hochladen** – eine kurze Beschreibung und die Meldung von XRlesbar reichen meist aus.

## Hinweise

**EN 16931:** XRlesbar ist eine Implementierung des semantischen Datenmodells der Europäischen Norm EN 16931-1:2017 und der Syntaxen nach CEN/TS 16931-2:2017. Die Wiedergabe erfolgt mit Zustimmung von CEN und DIN als Urheberrechtsinhaber. CEN und DIN haften nicht für Inhalt und Umsetzung dieser Anwendung; im Zweifel gelten die offiziellen Normtexte, die das DIN bereitstellt.

**KoSIT:** XRlesbar nutzt den KoSIT-Validator, die KoSIT-Konfiguration für XRechnung und die XRechnung-Visualisierung der Koordinierungsstelle für IT-Standards unverändert. XRlesbar ist kein offizielles Produkt der KoSIT.

**ZUGFeRD / Factur-X:** XRlesbar nutzt die Schemas und Prüfregeln aus dem ZUGFeRD-Infopaket unverändert. XRlesbar ist kein offizielles Produkt von FeRD (Forum elektronische Rechnung Deutschland bei der AWV e.V.) oder FNFE-MPE; die Namen ZUGFeRD und Factur-X bezeichnen nur das unterstützte Format.

**Lizenzen:** XRlesbar enthält Open-Source-Komponenten, unter anderem unter Apache 2.0, MPL 2.0 (Saxon-HE) und EUPL 1.2 (Prüfregeln der EN 16931). Die vollständigen Lizenzhinweise liegen jedem Release bei (`THIRD-PARTY-NOTICES`) und stecken auch in der JAR-Datei.

**Kostenlos und ohne Gewähr:** Das Prüfergebnis beruht auf den offiziellen Prüfregeln, ersetzt aber keine steuerliche oder rechtliche Prüfung. Es ist eine Hilfe, keine rechtsverbindliche Bewertung einer Rechnung.

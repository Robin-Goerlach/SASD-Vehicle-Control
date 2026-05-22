# SASD Vehicle Control – Lastenheft V0.1

**Projekt:** SASD Vehicle Control  
**Dokumenttyp:** Lastenheft  
**Version:** 0.1  
**Status:** Entwurf  
**Datum:** 2026-05-22  
**Auftraggeber-/Nutzerperspektive:** SASD-GmbH / kleine Unternehmen / Selbständige  
**Geplantes Schwesterprojekt:** SASD Finance Control  

---

## 1. Zweck dieses Dokuments

Dieses Lastenheft beschreibt aus Sicht des Auftraggebers und der späteren Anwender, was die Anwendung **SASD Vehicle Control** leisten soll. Es legt fachliche Ziele, gewünschte Funktionen, Qualitätsanforderungen, Abgrenzungen und Ausbaustufen fest.

Das Lastenheft beschreibt bewusst noch nicht im Detail, wie die Software technisch umgesetzt wird. Diese Umsetzung wird im Pflichtenheft konkretisiert. Dennoch enthält dieses Dokument bereits Hinweise auf gewünschte Eigenschaften wie lokale Datenhaltung, revisionsnahe Dokumentation, Dokumentenarchiv, Exportfähigkeit und spätere Integration mit **SASD Finance Control**.

---

## 2. Ausgangssituation

Kleine Unternehmen, Selbständige und Vereine besitzen häufig ein oder wenige Fahrzeuge, die geschäftlich, gemischt oder privat genutzt werden. Die damit verbundenen Informationen liegen oft verteilt vor:

- Tankquittungen im Handschuhfach oder als Papierbelege
- Werkstattrechnungen als PDF, Scan oder Ausdruck
- TÜV- und AU-Berichte in Ordnern
- Versicherungsunterlagen in E-Mails oder Akten
- Kilometerstände nur auf Rechnungen oder in einzelnen Notizen
- Wartungstermine im Kalender oder gar nicht dokumentiert
- Fahrten in Notizzetteln, Tabellen oder gar nicht sauber erfasst
- Fahrzeugkosten verstreut über Buchhaltung, Bankkonto und Belegablage

Dadurch fehlt ein zentraler Überblick über:

- tatsächliche Fahrzeugkosten
- Kraftstoffverbrauch
- Wartungs- und Reparaturhistorie
- fällige Termine und Fristen
- Belegvollständigkeit
- Zusammenhang zwischen Fahrzeugkosten und Finanzbuchhaltung
- Zustand und Historie eines Fahrzeugs

Für die SASD-GmbH besteht außerdem der Wunsch, langfristig eine eigene, lokale und vertrauenswürdige Verwaltungssoftware aufzubauen, die nicht von Cloud-Abos abhängig ist und deren Daten nachvollziehbar gespeichert werden.

---

## 3. Zielsetzung

Ziel ist die Entwicklung einer Anwendung zur strukturierten Verwaltung von Fahrzeugen, Fahrten, Tankvorgängen, Wartungen, Reparaturen, Dokumenten, Fristen und Kosten.

Die Anwendung soll insbesondere:

- Fahrzeuge zentral erfassen und verwalten
- Tankquittungen und Kraftstoffkosten dokumentieren
- Wartungen und Reparaturen nachvollziehbar speichern
- Belege und Fahrzeugdokumente revisionsnah archivieren
- Fristen und Wartungstermine sichtbar machen
- Fahrzeugkosten auswertbar machen
- eine spätere Verbindung zu SASD Finance Control ermöglichen
- lokal nutzbar sein
- auch für kleine Firmen ohne große IT-Infrastruktur geeignet sein

Die Anwendung soll nicht primär ein GPS-Flottenmanagement-System sein. Der Schwerpunkt liegt auf **Dokumentation, Nachvollziehbarkeit, Kostenkontrolle und Belegverwaltung**.

---

## 4. Produktvision

SASD Vehicle Control soll eine lokale, vertrauenswürdige KFZ-Verwaltung für kleine Unternehmen, Selbständige und Organisationen werden.

Die Anwendung soll langfristig Teil eines größeren **SASD Business Control Ecosystems** sein. Darin können verschiedene fachliche Verwaltungsbereiche miteinander verbunden werden, zum Beispiel:

- SASD Finance Control
- SASD Vehicle Control
- Vertragsverwaltung
- Dokumentenarchiv
- Lieferantenverwaltung
- Reporting
- Backup- und Auditfunktionen

Die erste Version soll jedoch bewusst klein, stabil und beherrschbar bleiben.

---

## 5. Zielgruppen

### 5.1 Primäre Zielgruppe

Die primäre Zielgruppe sind kleine Unternehmen, Selbständige und Freiberufler, die ein oder wenige Fahrzeuge verwalten müssen.

Beispiele:

- SASD-GmbH selbst
- kleine IT-Dienstleister
- Handwerker
- Beratungsunternehmen
- Einzelunternehmer
- kleine Fuhrparks
- Vereine mit Fahrzeugen
- Familienbetriebe

### 5.2 Sekundäre Zielgruppe

Sekundär kann die Anwendung auch für Privatpersonen interessant sein, die ihre Fahrzeugkosten und Wartungen sauber dokumentieren möchten.

### 5.3 Nicht primäre Zielgruppe

Nicht primär adressiert werden in der ersten Version:

- große Speditionen
- Lieferdienste mit Disposition
- Echtzeit-Flottenüberwachung
- GPS-Tracking-Unternehmen
- Taxibetriebe mit komplexer Schichtplanung
- Fahrzeugvermietungen mit umfangreicher Buchungslogik

---

## 6. Grundprinzipien

Die Anwendung soll nach folgenden Grundprinzipien entwickelt werden:

### 6.1 Einfachheit vor Überladung

Die Anwendung soll für kleine Unternehmen sofort verständlich sein. Sie soll nicht wie ein großes ERP-System wirken.

### 6.2 Dokumentation statt bloßer Datensammlung

Daten sollen nicht nur erfasst, sondern nachvollziehbar mit Belegen, Dokumenten und Historie verbunden werden.

### 6.3 Lokal nutzbar

Die Anwendung soll ohne zwingende Cloud-Anbindung nutzbar sein.

### 6.4 Revisionsnähe

Wichtige Vorgänge sollen nachvollziehbar bleiben. Belege sollen nicht still überschrieben oder unkontrolliert gelöscht werden.

### 6.5 Erweiterbarkeit

Die Anwendung soll später um weitere Funktionen ergänzt werden können, ohne die erste Version unnötig kompliziert zu machen.

### 6.6 Finance-Nähe

Fahrzeugkosten sollen perspektivisch mit Finanzdaten, Bankbewegungen, Lieferanten und Belegen verbunden werden können.

---

## 7. Abgrenzung zu anderen Anwendungstypen

### 7.1 Keine reine Tankbuch-App

Die Anwendung soll mehr leisten als nur Tankvorgänge und Verbrauch zu erfassen.

### 7.2 Kein klassisches GPS-Flottenmanagement

GPS-Tracking, Geofencing und Live-Ortung stehen nicht im Mittelpunkt und sind für die erste Version nicht vorgesehen.

### 7.3 Kein vollständiges ERP-System

SASD Vehicle Control soll keine vollständige Buchhaltung oder Warenwirtschaft ersetzen.

### 7.4 Kein garantiert finanzamtskonformes Fahrtenbuch in V1

Eine einfache Fahrtenverwaltung kann vorgesehen werden. Eine verbindliche Aussage zur steuerlichen Anerkennung als finanzamtskonformes Fahrtenbuch soll in der ersten Version ausdrücklich vermieden werden, solange die rechtlichen und technischen Anforderungen nicht vollständig umgesetzt und geprüft sind.

---

## 8. Nutzerrollen

### 8.1 Administrator

Der Administrator richtet die Anwendung ein, verwaltet Stammdaten, führt Backups durch und kann Systemeinstellungen ändern.

### 8.2 Sachbearbeiter / Verwaltung

Diese Rolle erfasst Fahrzeuge, Tankungen, Wartungen, Belege, Kosten und Fristen.

### 8.3 Fahrer

Ein Fahrer kann Fahrten, Kilometerstände, Tankvorgänge und einfache Hinweise erfassen. In einer späteren Version kann dies auch mobil erfolgen.

### 8.4 Geschäftsführung / Auswertung

Diese Rolle betrachtet Kosten, Reports, Fristen, Fahrzeugzustände und Entscheidungsgrundlagen.

### 8.5 Steuerberater / externe Auswertung

Ein Steuerberater soll perspektivisch Exporte, Belegpakete oder Auswertungen erhalten können. Ein direkter Zugriff ist in der ersten Version nicht zwingend erforderlich.

---

## 9. Fachliche Hauptbereiche

Die Anwendung soll folgende Hauptbereiche abdecken:

1. Fahrzeugverwaltung
2. Fahrer- und Nutzerverwaltung
3. Fahrtenverwaltung
4. Tankbuch
5. Wartung und Reparatur
6. Reifenverwaltung
7. Dokumentenarchiv
8. Verträge und wiederkehrende Kosten
9. Fristen und Erinnerungen
10. Kostenanalyse und Reporting
11. Export, Backup und Nachvollziehbarkeit
12. spätere Integration mit SASD Finance Control

---

# 10. Funktionale Anforderungen

---

## 10.1 Fahrzeugverwaltung

### 10.1.1 Ziel

Alle relevanten Stammdaten eines Fahrzeugs sollen zentral dokumentiert werden.

### 10.1.2 Muss-Anforderungen

Die Anwendung muss Fahrzeuge erfassen können.

Für jedes Fahrzeug sollen mindestens folgende Daten verwaltet werden können:

- interne Fahrzeugnummer oder eindeutige ID
- Kennzeichen
- Fahrzeugname oder Anzeigename
- Hersteller
- Modell
- Baujahr oder Erstzulassung
- Fahrzeugstatus
- Kraftstoffart oder Antriebsart
- aktueller Kilometerstand
- Datum der Erfassung
- Bemerkungen

Der Fahrzeugstatus soll mindestens unterscheiden können:

- aktiv
- außer Betrieb
- verkauft
- archiviert

Ein Fahrzeug soll nicht still gelöscht werden. Stattdessen soll mindestens eine Archivierung möglich sein.

### 10.1.3 Soll-Anforderungen

Zusätzlich sollen folgende Daten möglich sein:

- FIN / VIN
- Farbe
- Motorisierung
- Leistung
- Tankvolumen
- Verbrauchserwartung
- Fahrzeugklasse
- Eigentumsart: gekauft, geleast, finanziert, gemietet
- Kaufdatum
- Kaufpreis
- Verkäufer oder Händler
- Garantie bis
- TÜV/AU-Termine
- Versicherungshinweise

### 10.1.4 Kann-Anforderungen

Später können weitere Daten ergänzt werden:

- HSN/TSN
- CO₂-Wert
- Schadstoffklasse
- Umweltplakette
- Anhängelast
- Nutzlast
- Fahrzeugfotos
- Ausstattungsmerkmale
- Ladeinformationen bei Elektrofahrzeugen
- Batteriekapazität
- Wallbox-Zuordnung

---

## 10.2 Fahrer- und Nutzerverwaltung

### 10.2.1 Ziel

Fahrer sollen Fahrzeugen, Fahrten und Vorgängen zugeordnet werden können.

### 10.2.2 Muss-Anforderungen

In der ersten Version ist eine einfache Fahrerzuordnung wünschenswert, aber nicht zwingend so umfangreich wie eine Personalverwaltung.

Mindestens soll ein Fahrername bei Fahrten, Tankungen oder Wartungsmeldungen hinterlegt werden können.

### 10.2.3 Soll-Anforderungen

Die Anwendung soll Fahrer als eigene Stammdaten verwalten können:

- Name
- Kontaktinformationen
- aktiv/inaktiv
- Notizen
- bevorzugtes Fahrzeug

### 10.2.4 Kann-Anforderungen

Später können ergänzt werden:

- Führerscheinklasse
- Führerscheinprüfdatum
- Fahrerberechtigungen pro Fahrzeug
- digitale Fahrzeugübergabe
- Unterschriftsfunktion
- Fahrerhistorie

---

## 10.3 Fahrtenverwaltung

### 10.3.1 Ziel

Fahrten sollen dokumentiert werden können, insbesondere zur Nachvollziehbarkeit geschäftlicher Nutzung.

### 10.3.2 Muss-Anforderungen

Die Anwendung soll Fahrten erfassen können.

Für eine Fahrt sollen mindestens folgende Daten möglich sein:

- Fahrzeug
- Datum
- Fahrer
- Startort
- Zielort
- Kilometerstand Start
- Kilometerstand Ende
- gefahrene Kilometer
- Fahrtzweck
- Fahrtart: geschäftlich, privat, gemischt, unbekannt
- Notizen

Die gefahrenen Kilometer sollen aus Start- und Endkilometer berechnet werden können.

### 10.3.3 Soll-Anforderungen

Zusätzlich sollen möglich sein:

- Uhrzeit Start
- Uhrzeit Ende
- Projektbezug
- Kundenbezug
- Beleg- oder Dokumentenverknüpfung
- Zwischenziele
- Kostenstelle
- Plausibilitätsprüfung der Kilometerstände

### 10.3.4 Kann-Anforderungen

Später können ergänzt werden:

- wiederkehrende Fahrten
- mobile Erfassung
- GPS-gestützte Streckenvorschläge
- Kartenanzeige
- Export als Fahrtenbuch
- Änderungsprotokoll für steuerliche Nachvollziehbarkeit

### 10.3.5 Hinweis zur steuerlichen Nutzung

Die Anwendung soll in V1 nicht automatisch als finanzamtskonformes Fahrtenbuch beworben werden. Dafür wären besondere Anforderungen an Unveränderbarkeit, Zeitnähe, Änderungshistorie und rechtliche Prüfung notwendig.

---

## 10.4 Tankbuch

### 10.4.1 Ziel

Tankvorgänge sollen vollständig dokumentiert und mit Kosten, Kilometerständen und Belegen verknüpft werden.

### 10.4.2 Muss-Anforderungen

Ein Tankvorgang muss erfassbar sein mit:

- Fahrzeug
- Datum
- Kilometerstand
- Kraftstoffart
- getankte Menge
- Gesamtbetrag
- Tankstelle oder Lieferant
- Volltank ja/nein
- Belegverknüpfung
- Notizen

Die Anwendung soll Verbrauchswerte berechnen können, soweit dies fachlich sinnvoll ist.

### 10.4.3 Soll-Anforderungen

Zusätzlich sollen möglich sein:

- Preis pro Liter
- Zahlungsart
- Rechnungsnummer oder Bonnummer
- Ort der Tankstelle
- Fahrer
- Kostenstelle
- Projektbezug
- Teilbetankung markieren
- Warnung bei unplausiblem Verbrauch
- automatische Berechnung des Literpreises aus Gesamtbetrag und Literzahl

### 10.4.4 Kann-Anforderungen

Später können ergänzt werden:

- Tankkartenverwaltung
- Import von Tankkartenabrechnungen
- Durchschnittspreise je Monat
- Kraftstoffpreisvergleich
- Verbrauchsdiagramme
- CO₂-Schätzung
- AdBlue-Erfassung
- Strom-/Ladevorgänge für Elektrofahrzeuge

---

## 10.5 Ladevorgänge für Elektro- und Hybridfahrzeuge

### 10.5.1 Ziel

Die Anwendung soll perspektivisch auch Elektrofahrzeuge und Plug-in-Hybride unterstützen.

### 10.5.2 Muss-Anforderungen in V1

Für V1 ist eine vollständige Ladeverwaltung nicht zwingend erforderlich. Die Datenstruktur sollte jedoch nicht so eng gebaut werden, dass später nur klassische Kraftstoffe möglich sind.

### 10.5.3 Soll-Anforderungen für spätere Versionen

Später sollen Ladevorgänge erfasst werden können:

- Fahrzeug
- Datum
- Kilometerstand
- Ladeort
- kWh
- Preis pro kWh
- Gesamtbetrag
- Ladekarte
- Wallbox
- öffentlicher Ladeanbieter
- Beleg

### 10.5.4 Kann-Anforderungen

Später:

- Trennung Heimladung / öffentliche Ladung
- PV-Strom-Anteil
- Batteriestand Start/Ende
- Ladeverluste
- Wallbox-Import

---

## 10.6 Wartung und Reparaturen

### 10.6.1 Ziel

Wartungen und Reparaturen sollen nachvollziehbar dokumentiert werden.

### 10.6.2 Muss-Anforderungen

Die Anwendung muss Wartungs- und Reparaturvorgänge erfassen können.

Mindestens erforderlich:

- Fahrzeug
- Datum
- Kilometerstand
- Art des Vorgangs
- Beschreibung
- Werkstatt oder Lieferant
- Kosten
- Beleg/Rechnung
- Notizen

Typische Vorgangsarten:

- Inspektion
- Ölwechsel
- Bremsen
- Reifen
- Batterie
- TÜV/AU
- Reparatur allgemein
- Unfallreparatur
- Sonstiges

### 10.6.3 Soll-Anforderungen

Zusätzlich sollen möglich sein:

- Arbeitskosten
- Materialkosten
- Garantiebezug
- betroffene Baugruppe
- nächste Fälligkeit nach Datum
- nächste Fälligkeit nach Kilometerstand
- wiederkehrende Wartungsintervalle
- Status: geplant, durchgeführt, storniert, offen
- Dokumentenverknüpfungen

### 10.6.4 Kann-Anforderungen

Später:

- Wartungspläne pro Fahrzeugtyp
- Checklisten pro Wartungsart
- Erinnerung vor Erreichen des Kilometerintervalls
- Werkstattbewertung
- Kostenvergleich zwischen Werkstätten
- Fotodokumentation vor/nach Reparatur

---

## 10.7 Reifenverwaltung

### 10.7.1 Ziel

Reifen und Räder sollen langfristig nachvollziehbar verwaltet werden.

### 10.7.2 Muss-Anforderungen

Für V1 ist eine einfache Reifeninformation ausreichend. Reifenwechsel können zunächst als Wartungsvorgang erfasst werden.

### 10.7.3 Soll-Anforderungen

Die Anwendung soll später Reifensätze verwalten können:

- Fahrzeug
- Reifentyp: Sommer, Winter, Ganzjahr
- Hersteller
- Modell
- Größe
- Profiltiefe
- Kaufdatum
- Kosten
- Lagerort
- montiert ja/nein
- letzter Wechsel
- nächster geplanter Wechsel

### 10.7.4 Kann-Anforderungen

Später:

- Reifendruckhistorie
- Profiltiefenverlauf
- DOT-Nummer
- Felgeninformationen
- Einlagerungsbelege
- Erinnerung bei Alter oder Profiltiefe

---

## 10.8 Dokumentenarchiv

### 10.8.1 Ziel

Alle relevanten Dokumente zu Fahrzeugen und Fahrzeugkosten sollen zentral und nachvollziehbar gespeichert werden.

### 10.8.2 Muss-Anforderungen

Die Anwendung muss Dokumente verwalten können.

Mindestens sollen unterstützt werden:

- PDF-Dateien
- Bilder / Fotos
- Scans

Zu jedem Dokument sollen gespeichert werden:

- Dokumenttyp
- Originaldateiname
- Importdatum
- Dateigröße
- Hashwert, vorzugsweise SHA256
- Beschreibung
- Zuordnung zu Fahrzeug oder Vorgang

Dokumente sollen nicht still überschrieben werden. Bei gleichem Dateinamen oder gleichem Inhalt soll nachvollziehbar gehandelt werden.

### 10.8.3 Dokumenttypen

Mindestens sollen folgende Dokumenttypen vorgesehen werden:

- Tankquittung
- Werkstattrechnung
- TÜV-Bericht
- AU-Bericht
- Versicherungsdokument
- Leasingvertrag
- Kaufvertrag
- Zulassungsbescheinigung
- Foto
- Schadensdokumentation
- sonstiges Dokument

### 10.8.4 Soll-Anforderungen

Zusätzlich sollen möglich sein:

- Dokumentenvorschau
- Dokument öffnen
- mehrere Dokumente pro Vorgang
- freie Schlagworte
- Verknüpfung mit Tankung, Wartung, Vertrag, Fahrt oder Fahrzeug
- Duplikaterkennung über Hash
- Export eines Belegpakets

### 10.8.5 Kann-Anforderungen

Später:

- OCR-Erkennung
- automatische Klassifizierung
- automatische Betrags-/Datums-/Lieferantenerkennung
- Signaturprüfung
- revisionssicherer Speicherbereich
- Integration mit externem Dokumentenmanagement

---

## 10.9 Verträge und wiederkehrende Kosten

### 10.9.1 Ziel

Verträge und wiederkehrende Kosten rund um Fahrzeuge sollen sichtbar und kontrollierbar werden.

### 10.9.2 Muss-Anforderungen

In V1 soll mindestens die manuelle Erfassung wichtiger wiederkehrender Kosten möglich sein oder über Wartung/Kostenbuch abbildbar sein.

### 10.9.3 Soll-Anforderungen

Die Anwendung soll Verträge verwalten können:

- Versicherung
- Leasing
- Finanzierung
- Wartungsvertrag
- Schutzbrief
- Tankkarte
- Ladekarte
- Garantieverlängerung

Daten:

- Vertragspartner
- Vertragsnummer
- Beginn
- Ende
- Kündigungsfrist
- Kostenbetrag
- Zahlungsintervall
- zugeordnetes Fahrzeug
- Dokumente
- Erinnerung

### 10.9.4 Kann-Anforderungen

Später:

- automatische Kostenplanung
- Vertragsverlängerung
- Kündigungserinnerung
- Vergleich verschiedener Vertragskosten
- Übergabe an Finance Control

---

## 10.10 Fristen und Erinnerungen

### 10.10.1 Ziel

Wichtige Fristen sollen nicht vergessen werden.

### 10.10.2 Muss-Anforderungen

Die Anwendung muss fällige oder bald fällige Termine anzeigen können.

Mindestens relevante Fristen:

- TÜV/AU
- Inspektion
- Ölwechsel
- Reifenwechsel
- Versicherungsablauf
- Vertragsende

### 10.10.3 Soll-Anforderungen

Erinnerungen sollen nach Datum und/oder Kilometerstand möglich sein.

Status:

- geplant
- bald fällig
- fällig
- überfällig
- erledigt

Die Startseite soll kritische Fristen sichtbar machen.

### 10.10.4 Kann-Anforderungen

Später:

- E-Mail-Erinnerung
- Kalenderexport
- Windows-Benachrichtigung
- Erinnerungsprofile
- Eskalationshinweise

---

## 10.11 Kostenverwaltung

### 10.11.1 Ziel

Alle Fahrzeugkosten sollen nachvollziehbar erfasst und ausgewertet werden können.

### 10.11.2 Muss-Anforderungen

Kosten sollen mindestens aus folgenden Bereichen entstehen können:

- Tankungen
- Wartungen
- Reparaturen
- Verträge
- sonstige Kosten

Kosten sollen einem Fahrzeug zugeordnet werden können.

### 10.11.3 Soll-Anforderungen

Die Anwendung soll Kosten nach Kategorien auswerten können:

- Kraftstoff
- Reparatur
- Wartung
- Reifen
- Versicherung
- Steuer
- Leasing/Finanzierung
- Zubehör
- Gebühren
- sonstige Kosten

### 10.11.4 Kann-Anforderungen

Später:

- Kostenstellen
- Projektzuordnung
- Kundenbezug
- steuerliche Kategorien
- Export an Buchhaltung
- Verbindung zu Bankbuchungen

---

## 10.12 Reporting und Auswertung

### 10.12.1 Ziel

Die Anwendung soll Entscheidungsgrundlagen liefern.

### 10.12.2 Muss-Anforderungen

Mindestens sollen einfache Übersichten möglich sein:

- Fahrzeuge und Status
- Kosten je Fahrzeug
- Tankkosten
- Wartungskosten
- fällige Termine
- letzte Tankungen
- letzte Wartungen

### 10.12.3 Soll-Anforderungen

Weitere Auswertungen:

- Kosten pro Monat
- Kosten pro Jahr
- Kosten pro Kilometer
- Kraftstoffverbrauch
- durchschnittlicher Literpreis
- Reparaturkostenverlauf
- Wartungshistorie
- Belegvollständigkeit

### 10.12.4 Kann-Anforderungen

Später:

- Diagramme
- PDF-Berichte
- Jahresbericht für Steuerberater
- Vergleich mehrerer Fahrzeuge
- TCO-Berechnung
- Restwert-/Verkaufshistorie

---

## 10.13 Suche und Filter

### 10.13.1 Ziel

Daten sollen schnell auffindbar sein.

### 10.13.2 Muss-Anforderungen

Es soll eine Suche oder Filterung für zentrale Listen geben:

- Fahrzeuge
- Tankungen
- Wartungen
- Dokumente

### 10.13.3 Soll-Anforderungen

Filter nach:

- Fahrzeug
- Zeitraum
- Kostenart
- Dokumenttyp
- Status
- Fahrer
- Werkstatt/Lieferant

### 10.13.4 Kann-Anforderungen

Später:

- Volltextsuche über Notizen
- Suche über OCR-Text
- gespeicherte Filter
- Favoritenansichten

---

## 10.14 Importfunktionen

### 10.14.1 Ziel

Bestehende Daten sollen möglichst einfach übernommen werden können.

### 10.14.2 Muss-Anforderungen

Für V1 ist ein manueller Start ausreichend. Ein CSV-Import ist wünschenswert, aber nicht zwingend für die allererste lauffähige Version.

### 10.14.3 Soll-Anforderungen

Import aus:

- CSV-Dateien
- Tabellenkalkulationen über CSV
- vorhandene Tanklisten
- einfache Belegordner

### 10.14.4 Kann-Anforderungen

Später:

- Import aus Tankkartenabrechnungen
- Import aus Banking-Exporten
- Import aus anderer Fahrzeugsoftware
- OCR-gestützter Belegimport
- Drag-and-Drop-Belegimport

---

## 10.15 Exportfunktionen

### 10.15.1 Ziel

Die eigenen Daten sollen nicht eingeschlossen sein.

### 10.15.2 Muss-Anforderungen

Die Anwendung muss Exportfunktionen bieten:

- CSV-Export zentraler Tabellen
- JSON-Export für technische Weiterverarbeitung
- ZIP-Backup

### 10.15.3 Soll-Anforderungen

Zusätzlich:

- Markdown-Berichte
- Belegpaket mit Manifest
- Kostenübersichten
- Export pro Fahrzeug
- Export pro Zeitraum

### 10.15.4 Kann-Anforderungen

Später:

- PDF-Berichte
- DATEV-nahe Übergabedateien
- Finance-Control-Export
- Steuerberaterpaket

---

## 10.16 Backup und Wiederherstellung

### 10.16.1 Ziel

Datenverlust soll vermieden werden.

### 10.16.2 Muss-Anforderungen

Die Anwendung muss ein Backup der Daten ermöglichen.

Das Backup soll mindestens enthalten:

- Datenbank
- Dokumente
- Manifest
- Zeitstempel

### 10.16.3 Soll-Anforderungen

Zusätzlich:

- ZIP-Backup
- Prüfsummen
- Wiederherstellung aus Backup
- Sicherheitsbackup vor Import oder Restore

### 10.16.4 Kann-Anforderungen

Später:

- automatische Backups
- Backup-Erinnerung
- verschlüsselte Backups
- Backup auf Netzlaufwerk
- Backup-Historie

---

## 10.17 Audit, Nachvollziehbarkeit und Datenintegrität

### 10.17.1 Ziel

Wichtige Datenänderungen sollen nachvollziehbar sein.

### 10.17.2 Muss-Anforderungen

Für zentrale Daten soll nachvollziehbar sein:

- wann ein Datensatz erstellt wurde
- wann er geändert wurde
- ob er archiviert wurde

### 10.17.3 Soll-Anforderungen

Zusätzlich:

- Änderungsprotokoll für wichtige Vorgänge
- keine stille Löschung wichtiger Daten
- Archivierung statt Löschung
- Dokumenthashes
- Plausibilitätsprüfungen

### 10.17.4 Kann-Anforderungen

Später:

- vollständiges Audit-Log
- Änderungsvergleich alter/neuer Werte
- Benutzerbezogene Änderungshistorie
- Manipulationserkennung
- Export eines Audit-Protokolls

---

## 10.18 Integration mit SASD Finance Control

### 10.18.1 Ziel

SASD Vehicle Control soll langfristig mit SASD Finance Control zusammenarbeiten.

### 10.18.2 Muss-Anforderungen

In V1 muss die Integration noch nicht technisch umgesetzt sein. Die Datenstruktur soll aber so geplant werden, dass eine spätere Integration möglich bleibt.

### 10.18.3 Soll-Anforderungen

Später sollen verknüpft werden können:

- Tankquittung ↔ Zahlung
- Werkstattrechnung ↔ Lieferant
- Fahrzeugvertrag ↔ Vertragsverwaltung
- Fahrzeugkosten ↔ Kostenkategorie
- Beleg ↔ Dokumentenarchiv
- Fahrzeug ↔ Kostenstelle

### 10.18.4 Kann-Anforderungen

Später:

- gemeinsames Lieferantenverzeichnis
- gemeinsames Dokumentenarchiv
- gemeinsames Reporting
- Bankbuchungsabgleich
- Steuerberaterexport
- Übergabe an Buchhaltung

---

## 10.19 Benutzeroberfläche

### 10.19.1 Ziel

Die Anwendung soll übersichtlich, ruhig und professionell wirken.

### 10.19.2 Muss-Anforderungen

Die Oberfläche muss die wichtigsten Bereiche gut erreichbar machen:

- Dashboard
- Fahrzeuge
- Tankbuch
- Wartung/Reparatur
- Dokumente
- Fristen
- Reports

### 10.19.3 Soll-Anforderungen

Gewünscht sind:

- klare Navigation
- tabellarische Übersichten
- Detailansichten
- verständliche Formulare
- Such- und Filterbereiche
- Kontextmenüs
- Doppelklick-Aktionen
- verständliche Fehlermeldungen

### 10.19.4 Kann-Anforderungen

Später:

- mobile Weboberfläche
- responsive Layout
- dunkles Design
- anpassbare Dashboards
- Favoriten

---

## 10.20 Mobile Nutzung

### 10.20.1 Ziel

Tankquittungen und Fahrten entstehen häufig unterwegs. Mobile Nutzung ist daher langfristig sehr wertvoll.

### 10.20.2 Muss-Anforderungen in V1

Mobile Nutzung ist für V1 nicht zwingend erforderlich.

### 10.20.3 Soll-Anforderungen für spätere Versionen

Später sollen möglich sein:

- Tankung unterwegs erfassen
- Belegfoto aufnehmen
- Kilometerstand erfassen
- Fahrt starten/beenden
- einfache mobile Oberfläche

### 10.20.4 Kann-Anforderungen

Später:

- Offline-Modus
- Synchronisation
- QR-Code-Upload
- Progressive Web App

---

## 10.21 OCR und Automatisierung

### 10.21.1 Ziel

Manuelle Erfassung soll langfristig reduziert werden.

### 10.21.2 Muss-Anforderungen in V1

OCR ist in V1 nicht erforderlich.

### 10.21.3 Soll-Anforderungen für spätere Versionen

Später sollen Belege automatisch ausgewertet werden können:

- Datum
- Betrag
- Lieferant
- Liter / kWh
- Kraftstoffart
- Rechnungsnummer

### 10.21.4 Kann-Anforderungen

Später:

- KI-gestützte Klassifikation
- automatische Vorschläge für Kostenkategorien
- Erkennung von Duplikaten
- Plausibilitätsprüfung

---

## 10.22 GPS, OBD-II und Telematik

### 10.22.1 Ziel

Technische Fahrzeugdaten können langfristig interessant sein, stehen aber nicht im Fokus der ersten Version.

### 10.22.2 Muss-Anforderungen in V1

Keine.

### 10.22.3 Soll-Anforderungen für spätere Versionen

Möglich wären später:

- OBD-II-Import
- Kilometerstand aus Fahrzeugdaten
- Fehlercodes
- Batteriezustand
- Serviceindikatoren

### 10.22.4 Nicht-Ziel in V1

Nicht geplant für V1:

- Live-GPS-Tracking
- Geofencing
- Fahrerüberwachung
- automatische permanente Ortung

Diese Funktionen sind datenschutzkritisch und erhöhen die Komplexität erheblich.

---

# 11. Nichtfunktionale Anforderungen

---

## 11.1 Bedienbarkeit

Die Anwendung soll ohne umfangreiche Schulung bedienbar sein. Formulare sollen verständlich beschriftet sein. Fehler sollen nachvollziehbar erklärt werden.

---

## 11.2 Zuverlässigkeit

Die Anwendung soll robust mit Eingabefehlern umgehen. Datenverlust soll vermieden werden. Kritische Vorgänge wie Import, Restore oder Löschung sollen abgesichert sein.

---

## 11.3 Datenqualität

Die Anwendung soll Plausibilitätsprüfungen unterstützen, z. B.:

- Kilometerstand darf nicht unlogisch sinken, ohne Warnung
- Tankmenge darf nicht negativ sein
- Kosten dürfen nicht negativ sein
- Endkilometer müssen größer oder gleich Startkilometer sein
- Pflichtfelder müssen gefüllt sein

---

## 11.4 Datenschutz

Die Anwendung kann personenbezogene Daten und Bewegungsdaten enthalten. Daher sollen Daten lokal kontrollierbar bleiben. Rollen und Berechtigungen sind langfristig sinnvoll.

---

## 11.5 Sicherheit

Wichtige Anforderungen:

- keine unkontrollierte Cloudpflicht
- sichere lokale Speicherung
- keine Klartextpasswörter, falls Benutzerkonten eingeführt werden
- kontrollierter Dokumentenzugriff
- Backupmöglichkeit

---

## 11.6 Erweiterbarkeit

Die Anwendung soll so geplant werden, dass später weitere Module ergänzt werden können:

- Finance-Integration
- OCR
- Mobile Erfassung
- Elektrofahrzeuge
- Vertragsverwaltung
- Steuerberaterexport

---

## 11.7 Wartbarkeit

Das Projekt soll langfristig wartbar sein. Fachlogik, Oberfläche und Datenzugriff sollen sauber getrennt werden.

---

## 11.8 Portabilität

Die erste Version darf als Windows-Desktop-Anwendung geplant werden. Langfristig soll geprüft werden, ob Web-, Linux- oder plattformübergreifende Varianten sinnvoll sind.

---

## 11.9 Performance

Für kleine Datenmengen muss die Anwendung sehr schnell reagieren. Typische Szenarien:

- 1 bis 20 Fahrzeuge
- mehrere tausend Tankungen
- mehrere tausend Dokumente
- viele Jahre Historie

---

## 11.10 Nachvollziehbarkeit

Die Anwendung soll eine nachvollziehbare Historie wichtiger Vorgänge ermöglichen. Besonders Belege, Wartungen, Fahrten und Kosten dürfen nicht unbemerkt verändert oder entfernt werden.

---

# 12. Daten- und Informationsobjekte

Die folgenden fachlichen Objekte sollen im System berücksichtigt werden:

- Fahrzeug
- Fahrer
- Fahrt
- Tankung
- Ladevorgang
- Wartung
- Reparatur
- Reifensatz
- Dokument
- Vertrag
- Erinnerung
- Lieferant/Werkstatt
- Kostenkategorie
- Kostenstelle
- Exportpaket
- Backup
- Audit-Eintrag

---

# 13. Muss-/Soll-/Kann-Zusammenfassung

## 13.1 Muss für V1

- Fahrzeugverwaltung
- Tankbuch
- Wartung/Reparatur
- Dokumentenarchiv mit Hash
- Fristenübersicht
- einfache Kostenübersichten
- Export mindestens CSV/JSON
- ZIP-Backup
- Archivierung statt stiller Löschung
- lokale Datenhaltung
- klare Navigation

## 13.2 Soll für V1 oder frühe V1.x

- Fahrtenverwaltung
- einfache Fahrerzuordnung
- Vertrags-/Kostenverwaltung
- Markdown-Export
- Belegpaket mit Manifest
- Suche und Filter
- Plausibilitätsprüfungen
- Kosten pro Kilometer
- Erinnerungen nach Kilometerstand
- Kontextmenüs und Doppelklick-Aktionen

## 13.3 Kann für spätere Versionen

- Mobile Erfassung
- OCR
- PDF-Berichte
- Finance-Control-Integration
- Kalenderexport
- E-Mail-Erinnerungen
- Elektrofahrzeug-Ladeverwaltung
- OBD-II-Import
- GPS-gestützte Fahrterfassung
- vollständiges Audit-Log
- Benutzer- und Rollenverwaltung

---

# 14. Priorisierte Versionen

---

## 14.1 Version 0.1 – Dokumentation und Projektbasis

Ziele:

- Repository vorbereiten
- README erstellen
- Screenshot-Mockup einbinden
- Lastenheft erstellen
- Pflichtenheft erstellen
- Roadmap erstellen
- erstes Datenmodell skizzieren

---

## 14.2 Version 0.2 – Anwendungsschale

Ziele:

- lauffähige Desktop-Anwendung
- Navigation
- Logging
- Konfiguration
- Fehlerbehandlung
- SQLite-Grundlage
- Teststruktur

---

## 14.3 Version 0.3 – Fahrzeugstammdaten

Ziele:

- Fahrzeuge anlegen, bearbeiten, archivieren
- Fahrzeugliste
- Fahrzeugdetails
- einfache Suche

---

## 14.4 Version 0.4 – Tankbuch

Ziele:

- Tankungen erfassen
- Verbrauch berechnen
- Kosten auswerten
- Beleg zuordnen

---

## 14.5 Version 0.5 – Wartung und Reparatur

Ziele:

- Wartungen erfassen
- Reparaturen erfassen
- Werkstätten/Lieferanten hinterlegen
- Dokumente verknüpfen

---

## 14.6 Version 0.6 – Dokumentenarchiv

Ziele:

- Dokumentimport
- Hashbildung
- Dokumenttypen
- Dokumentverknüpfung
- Dokumentensuche

---

## 14.7 Version 0.7 – Fristen und Erinnerungen

Ziele:

- TÜV/AU
- Inspektion
- Ölwechsel
- Reifenwechsel
- Vertragsfristen
- Dashboard-Hinweise

---

## 14.8 Version 0.8 – Reports und Exporte

Ziele:

- Kostenreports
- Verbrauchsreports
- CSV/JSON/Markdown-Export
- Belegpakete

---

## 14.9 Version 1.0 – Erste stabile Version

Ziele:

- stabile lokale KFZ-Verwaltung
- Fahrzeug, Tankung, Wartung, Dokument, Frist, Report
- Backup/Restore
- robuste Bedienung
- ausreichend Tests und Dokumentation

---

# 15. Abnahmekriterien

Eine erste stabile Version kann als abnahmefähig gelten, wenn:

- Fahrzeuge angelegt und archiviert werden können
- Tankungen mit Beleg erfasst werden können
- Wartungen/Reparaturen mit Beleg erfasst werden können
- Dokumente mit Hash gespeichert werden
- Fristen sichtbar sind
- Kosten je Fahrzeug ausgewertet werden können
- Daten exportiert werden können
- ein Backup erstellt und wiederhergestellt werden kann
- die Anwendung ohne Datenverlust neu gestartet werden kann
- grundlegende Fehlerfälle verständlich behandelt werden
- keine wichtigen Datensätze still gelöscht werden

---

# 16. Risiken und offene Punkte

## 16.1 Steuerliche Anerkennung Fahrtenbuch

Eine steuerlich anerkannte Fahrtenbuchfunktion ist komplex. Sie sollte nicht leichtfertig versprochen werden.

## 16.2 Datenschutz bei Fahrten und GPS

Fahrten enthalten potenziell sensible Bewegungsdaten. GPS-Funktionen müssen besonders vorsichtig geplant werden.

## 16.3 Dokumentenablage

Es muss entschieden werden, ob Dokumente direkt in der Datenbank, im Dateisystem oder hybrid gespeichert werden.

## 16.4 Integration mit Finance Control

Die Integration ist strategisch wichtig, sollte aber nicht die erste Version überladen.

## 16.5 Mobile Nutzung

Mobile Belegerfassung ist sehr nützlich, erhöht aber Architektur- und Sicherheitsanforderungen.

---

# 17. Nicht-Ziele der ersten Version

Für die erste Version ausdrücklich nicht vorgesehen:

- vollständige Buchhaltung
- DATEV-Integration
- automatische Bankbuchungszuordnung
- Live-GPS-Tracking
- Disposition von Fahrern
- Routenoptimierung
- Telematikplattform
- OBD-II-Live-Anbindung
- Cloud-Synchronisation
- Mandantenfähiges SaaS-System
- garantierte steuerliche Fahrtenbuchanerkennung

---

# 18. Strategische Einordnung

SASD Vehicle Control soll als eigenständiges Projekt und Repository entstehen, aber bewusst als Schwesterprojekt zu SASD Finance Control geplant werden.

Empfohlene Projektpositionierung:

> SASD Vehicle Control ist eine lokale, dokumentenorientierte Fahrzeug-, Kosten- und Belegverwaltung für kleine Unternehmen, Selbständige und Organisationen.

Der besondere Wert liegt in:

- lokaler Kontrolle
- sauberer Dokumentation
- Belegnähe
- Hashing und Nachvollziehbarkeit
- klarer Kostenübersicht
- späterer Finance-Control-Anbindung
- einfacher Bedienbarkeit

---

# 19. Glossar

| Begriff | Bedeutung |
|---|---|
| Fahrzeug | Verwaltetes KFZ, Anhänger oder perspektivisch anderes Mobilitätsobjekt |
| Tankung | Vorgang zur Erfassung von Kraftstoffbezug |
| Ladevorgang | Vorgang zur Erfassung elektrischer Energie bei E-Fahrzeugen |
| Wartung | Geplanter Servicevorgang zur Erhaltung des Fahrzeugs |
| Reparatur | Behebung eines Defekts oder Schadens |
| Dokument | Datei, Scan, Foto oder PDF mit Nachweischarakter |
| Hash | Prüfsumme zur Erkennung von Dateiänderungen oder Duplikaten |
| Frist | Datum oder Kilometerstand, zu dem etwas fällig wird |
| Reminder | Erinnerung an eine Frist oder Aufgabe |
| Finance Control | Schwesterprojekt zur Finanzverwaltung der SASD-GmbH |

---

# 20. Zusammenfassung

SASD Vehicle Control soll keine überladene Flottenplattform werden, sondern eine solide, lokale und vertrauenswürdige KFZ-Verwaltung mit Schwerpunkt auf Dokumentation, Belegen, Kosten und Nachvollziehbarkeit.

Die erste Version soll bewusst klein starten, aber alle Grundlagen enthalten, um später Finance-Integration, mobile Belegerfassung, OCR, Elektrofahrzeuge und weitergehende Auswertungen sauber ergänzen zu können.

Das Lastenheft bildet die fachliche Grundlage für die weitere Ausarbeitung im Pflichtenheft, Datenmodell, UI-Konzept und der Entwicklungsroadmap.

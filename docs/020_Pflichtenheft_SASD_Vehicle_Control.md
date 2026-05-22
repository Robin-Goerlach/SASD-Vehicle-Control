# SASD Vehicle Control – Pflichtenheft V0.1

**Projekt:** SASD Vehicle Control  
**Einordnung:** Schwesterprojekt zu SASD Finance Control innerhalb des geplanten SASD Business Control Ecosystems  
**Dokumenttyp:** Pflichtenheft / technische und fachliche Umsetzungsspezifikation  
**Stand:** 2026-05-21  
**Status:** Entwurf für MVP/V1-Planung  
**Zielplattform:** Lokale Desktop-Anwendung, später optional erweiterbar  
**Vorgeschlagener Technologie-Stack:** C# / .NET 8+, SQLite, xUnit, Markdown-/CSV-/JSON-Export  

---

## 1. Zweck des Dokuments

Dieses Pflichtenheft beschreibt die geplante Umsetzung von **SASD Vehicle Control**. Die Anwendung soll Fahrzeuge, Fahrten, Tankvorgänge, Wartungen, Reparaturen, Belege, Fristen und Kosten nachvollziehbar dokumentieren. Ziel ist keine klassische GPS-Flottenlösung, sondern eine lokale, vertrauenswürdige und dokumentenorientierte KFZ-Verwaltung mit starkem Bezug zu Kostenkontrolle, Nachweisführung und späterer Integration in **SASD Finance Control**.

Das Pflichtenheft legt fest, welche Funktionen in der ersten stabilen Version vorgesehen sind, welche Anforderungen an Datenmodell, Architektur, Sicherheit, Auditierbarkeit, Export, Backup und spätere Erweiterbarkeit bestehen und welche Funktionen bewusst erst für spätere Versionen vorgesehen werden.

---

## 2. Produktvision

**SASD Vehicle Control** soll eine schlanke, robuste und nachvollziehbare KFZ-Verwaltung für kleine Unternehmen, Selbständige, Vereine und technisch orientierte Anwender werden. Die Anwendung soll helfen, Fahrzeugkosten und Fahrzeugdokumente nicht nur zu sammeln, sondern strukturiert auszuwerten und bei Bedarf gegenüber Buchhaltung, Steuerberater, Versicherung oder Werkstatt nachvollziehbar vorzulegen.

Der besondere Fokus liegt auf:

- lokaler Datenhaltung ohne Cloud-Zwang,
- revisionsnaher Beleg- und Dokumentenverwaltung,
- klarer Trennung von Fahrzeug-, Kosten- und Dokumentendaten,
- einfacher Bedienbarkeit,
- späterer Anbindung an SASD Finance Control,
- langfristiger Erweiterbarkeit zu einem modularen SASD Business Control Ecosystem.

---

## 3. Abgrenzung

### 3.1 Was SASD Vehicle Control leisten soll

Die Anwendung soll:

- Fahrzeuge verwalten,
- Fahrten dokumentieren,
- Tankbelege und Tankvorgänge erfassen,
- Wartungen und Reparaturen dokumentieren,
- Fahrzeugdokumente revisionsnah speichern,
- Fristen und Erinnerungen verwalten,
- Kosten pro Fahrzeug auswerten,
- Daten exportieren und sichern,
- eine spätere Integration mit SASD Finance Control vorbereiten.

### 3.2 Was SASD Vehicle Control zunächst nicht leisten soll

In V1 soll die Anwendung bewusst **nicht** leisten:

- GPS-Live-Tracking,
- automatische Fahrterkennung,
- OBD-II-Anbindung,
- Routenoptimierung,
- Fuhrpark-Disposition,
- Fahrer-App mit Echtzeitdaten,
- komplexe Multi-Mandanten-Cloud-Plattform,
- vollständige Buchhaltung,
- direkte DATEV-Schnittstelle,
- OCR-Pflichtfunktion,
- rechtsverbindliche Garantie für finanzamtskonformes Fahrtenbuch.

Diese Punkte können später geprüft werden, sollen aber die erste stabile Version nicht überladen.

---

## 4. Zielgruppen

### 4.1 Primäre Zielgruppen

- SASD-GmbH intern,
- kleine Unternehmen mit einem oder wenigen Fahrzeugen,
- Selbständige und Freiberufler,
- Vereine,
- private Anwender mit hohem Dokumentationsanspruch.

### 4.2 Sekundäre Zielgruppen

- kleine Handwerksbetriebe,
- Hausverwaltungen,
- Dienstleister mit Servicefahrzeugen,
- Personen, die Fahrzeugkosten für Steuerberater oder Buchhaltung vorbereiten müssen.

---

## 5. Grundsätzliche Systemprinzipien

### 5.1 Lokale Kontrolle

Die erste Version soll lokal funktionieren. Daten werden standardmäßig in einer lokalen SQLite-Datenbank gespeichert. Dokumente werden lokal in einer strukturierten Ablage verwaltet.

### 5.2 Nachvollziehbarkeit

Wichtige Datensätze sollen nicht still gelöscht werden. Löschvorgänge sollen, soweit fachlich sinnvoll, als Archivierung umgesetzt werden. Dokumente sollen beim Import gehasht werden, damit später erkennbar ist, ob eine Datei verändert wurde.

### 5.3 Keine Geschäftslogik in der UI

Die Benutzeroberfläche darf keine zentrale Geschäftslogik enthalten. Validierung, Berechnung, Archivierung, Hashing, Import, Export und fachliche Regeln gehören in Domain-, Application- oder Infrastructure-Schichten.

### 5.4 Kleine verständliche Klassen

Die Anwendung soll aus kleinen, nachvollziehbaren Klassen bestehen. Komplexe Klassen mit zu vielen Verantwortlichkeiten sind zu vermeiden.

### 5.5 Dokumentationsfreundlichkeit

Öffentliche Klassen, Services und zentrale Methoden sollen XML-Kommentare erhalten. Das Projekt soll so dokumentiert werden, dass spätere Erweiterungen nachvollziehbar möglich sind.

---

## 6. Fachliche Hauptmodule

Die Anwendung wird in folgende fachliche Module gegliedert:

1. Fahrzeugverwaltung
2. Fahrerverwaltung
3. Fahrtenbuch / Fahrtendokumentation
4. Tankbuch
5. Wartung und Reparaturen
6. Dokumentenarchiv
7. Fristen und Erinnerungen
8. Kosten und Auswertungen
9. Verträge und wiederkehrende Kosten
10. Export und Backup
11. Audit und Änderungsnachvollziehbarkeit
12. Vorbereitung der Finance-Control-Integration

---

## 7. Fahrzeugverwaltung

### 7.1 Ziel

Die Fahrzeugverwaltung bildet die fachliche Grundlage aller weiteren Module. Jeder Tankvorgang, jede Fahrt, jede Reparatur und jedes Dokument wird mindestens einem Fahrzeug zugeordnet.

### 7.2 Pflichtfunktionen V1

Die Anwendung muss Fahrzeuge anlegen, bearbeiten, anzeigen und archivieren können.

Folgende Stammdaten sollen vorgesehen werden:

- interne Fahrzeug-ID,
- Anzeigename / Fahrzeugname,
- Kennzeichen,
- Hersteller,
- Modell,
- Variante / Ausstattung,
- Baujahr,
- Erstzulassung,
- Fahrzeug-Identifizierungsnummer / FIN / VIN,
- Kraftstoffart,
- Getriebeart,
- Leistung,
- Hubraum, falls relevant,
- Farbe,
- aktueller Kilometerstand,
- Kaufdatum,
- Kaufpreis,
- Besitzart: Eigentum, Leasing, Finanzierung, Miete, anderes,
- Status: aktiv, verkauft, stillgelegt, archiviert,
- Notizen.

### 7.3 Fahrzeugstatus

Ein Fahrzeug darf nicht hart gelöscht werden, wenn bereits abhängige Datensätze existieren. In diesem Fall ist eine Archivierung vorzunehmen. Archivierte Fahrzeuge werden standardmäßig aus aktiven Listen ausgeblendet, bleiben aber für Reports und Nachweise erhalten.

### 7.4 Kilometerstandregeln

Die Anwendung soll Kilometerstände plausibilisieren. Ein neuer Kilometerstand darf grundsätzlich nicht kleiner sein als der zuletzt bekannte Kilometerstand, außer der Benutzer bestätigt dies ausdrücklich mit Begründung. Solche Korrekturen sollen protokolliert werden.

### 7.5 Spätere Erweiterungen

Für spätere Versionen sind folgende Erweiterungen vorzusehen:

- Fahrzeugbilder,
- Reifen- und Felgenzuordnung,
- technische Ausstattung,
- Garantieinformationen,
- Umweltplakette,
- Emissionsklasse,
- Elektro-/Hybrid-spezifische Daten,
- mehrere Kilometerzählerquellen.

---

## 8. Fahrerverwaltung

### 8.1 Ziel

Die Fahrerverwaltung erlaubt die Zuordnung von Fahrten, Fahrzeugübergaben und ggf. Verantwortlichkeiten zu Personen.

### 8.2 Pflichtfunktionen V1

In V1 soll mindestens eine einfache Fahrerverwaltung vorgesehen werden, auch wenn sie zunächst optional genutzt werden kann.

Datenfelder:

- Fahrer-ID,
- Name,
- E-Mail optional,
- Telefon optional,
- Führerscheinklasse optional,
- Führerschein geprüft am optional,
- aktiv/inaktiv,
- Notizen.

### 8.3 Datenschutz

Fahrerdaten sind personenbezogene Daten. Die Anwendung soll nur die notwendigen Informationen speichern. Standort- oder Bewegungsprofile dürfen in V1 nicht automatisch erzeugt werden.

---

## 9. Fahrtendokumentation

### 9.1 Ziel

Die Fahrtendokumentation soll geschäftliche und private Fahrten nachvollziehbar erfassen. Sie soll für Kosten- und Nutzungsübersichten geeignet sein. Eine spätere Erweiterung Richtung steuerlich strengeres Fahrtenbuch soll vorbereitet werden.

### 9.2 Pflichtfunktionen V1

Eine Fahrt soll erfassen können:

- Fahrzeug,
- Fahrer optional,
- Datum,
- Startzeit optional,
- Endzeit optional,
- Startort,
- Zielort,
- Zweck der Fahrt,
- Fahrtart: geschäftlich, privat, Arbeitsweg, gemischt, sonstige,
- Kilometerstand Start,
- Kilometerstand Ende,
- automatisch berechnete Kilometer,
- Projekt-/Kundenbezug optional,
- Notizen.

### 9.3 Fachliche Regeln

- Kilometer Ende muss größer oder gleich Kilometer Start sein.
- Die gefahrenen Kilometer werden berechnet, dürfen aber bei Sonderfällen mit Begründung korrigiert werden.
- Nachträgliche Änderungen an Fahrten sollen protokolliert werden.
- Fahrten dürfen nicht still gelöscht werden, sobald sie Teil eines Reports oder Exports waren.

### 9.4 Steuerliche Vorsicht

Die Anwendung darf in V1 nicht behaupten, automatisch ein finanzamtskonformes Fahrtenbuch zu erzeugen. Stattdessen soll die Dokumentation formulieren, dass sie eine strukturierte Fahrtendokumentation bietet, die später um strengere Audit- und Sperrmechanismen erweitert werden kann.

---

## 10. Tankbuch

### 10.1 Ziel

Das Tankbuch soll Kraftstoffkosten, Verbrauch und Tankbelege nachvollziehbar erfassen.

### 10.2 Pflichtfunktionen V1

Ein Tankvorgang soll erfassen:

- Fahrzeug,
- Datum,
- Uhrzeit optional,
- Kilometerstand,
- Tankstelle / Lieferant,
- Ort,
- Kraftstoffart,
- Liter,
- Preis pro Liter,
- Gesamtbetrag,
- Währung,
- Volltank ja/nein,
- Teilbetankung ja/nein,
- Zahlungsart optional,
- Belegverknüpfung,
- Notizen.

### 10.3 Berechnungen

Die Anwendung soll berechnen:

- Verbrauch pro 100 km, soweit möglich,
- Kosten pro Kilometer,
- durchschnittlicher Literpreis,
- Kraftstoffkosten pro Monat,
- Kraftstoffkosten pro Fahrzeug,
- Abweichungen zum Durchschnitt.

### 10.4 Plausibilitätsprüfungen

Die Anwendung soll warnen bei:

- Kilometerstand kleiner als vorheriger Kilometerstand,
- unrealistisch hohem Verbrauch,
- unrealistisch niedrigem Verbrauch,
- Betrag passt nicht zu Liter x Preis pro Liter,
- Tankvorgang ohne Fahrzeug,
- Tankvorgang ohne Beleg, sofern Belegpflicht aktiviert ist.

### 10.5 Belegpflicht optional

Für SASD-interne Nutzung kann eine Einstellung vorgesehen werden, ob Tankvorgänge ohne Beleg erlaubt sind. Wenn kein Beleg vorhanden ist, soll ein Grund dokumentiert werden können.

---

## 11. Wartung und Reparaturen

### 11.1 Ziel

Das Modul Wartung und Reparaturen soll technische Ereignisse, Werkstattbesuche, Ersatzteile, Rechnungen und Folgetermine dokumentieren.

### 11.2 Pflichtfunktionen V1

Eine Wartung oder Reparatur soll erfassen:

- Fahrzeug,
- Datum,
- Kilometerstand,
- Typ: Wartung, Reparatur, Inspektion, TÜV/AU, Reifen, Unfall, Sonstiges,
- Kategorie,
- Beschreibung,
- Werkstatt / Lieferant,
- Kosten netto optional,
- Umsatzsteuer optional,
- Kosten brutto,
- Beleg / Rechnung,
- nächste Fälligkeit nach Datum,
- nächste Fälligkeit nach Kilometerstand,
- Notizen.

### 11.3 Standardkategorien

Die Anwendung soll Standardkategorien vorschlagen:

- Ölwechsel,
- Inspektion,
- TÜV/AU,
- Bremsen,
- Reifenwechsel,
- Reifenanschaffung,
- Batterie,
- Scheibenwischer,
- Beleuchtung,
- Karosserie,
- Unfallreparatur,
- Elektrik,
- Softwareupdate,
- Klimaanlage,
- Sonstiges.

### 11.4 Wartungsintervalle

Die Anwendung soll zu einer Wartung optional Folgetermine erzeugen können, zum Beispiel:

- nächster Ölwechsel in 12 Monaten oder 15.000 km,
- nächste Inspektion in 24 Monaten,
- nächster TÜV-Termin,
- Reifenwechsel saisonal.

### 11.5 Reparaturhistorie

Für jedes Fahrzeug soll eine chronologische Reparatur- und Wartungshistorie angezeigt werden können.

---

## 12. Reifenverwaltung

### 12.1 Einordnung

Die Reifenverwaltung ist fachlich sinnvoll, aber für V1 optional. Sie sollte im Datenmodell vorbereitet werden, kann aber als vollständige UI-Funktion in V2 umgesetzt werden.

### 12.2 Geplante Funktionen

- Reifensatz anlegen,
- Sommerreifen/Winterreifen/Ganzjahresreifen,
- Hersteller,
- Modell,
- Größe,
- DOT,
- Profiltiefe,
- Kaufdatum,
- Kaufpreis,
- Einlagerungsort,
- montiert ja/nein,
- Fahrzeugzuordnung,
- Wechselhistorie.

---

## 13. Dokumentenarchiv

### 13.1 Ziel

Das Dokumentenarchiv ist ein Kernmerkmal des Systems. Es soll Belege und Nachweise nicht nur verlinken, sondern strukturiert, auffindbar und prüfbar speichern.

### 13.2 Pflichtfunktionen V1

Die Anwendung muss Dokumente importieren können. Unterstützt werden sollen mindestens:

- PDF,
- JPG,
- PNG,
- optional TXT/CSV/JSON für technische Nachweise.

Zu jedem Dokument werden gespeichert:

- Dokument-ID,
- Dokumenttyp,
- Originaldateiname,
- gespeicherter Dateiname,
- Speicherpfad,
- MIME-Type,
- Dateigröße,
- SHA256-Hash,
- Importdatum,
- importiert von optional,
- Beschreibung,
- Verknüpfungen zu Fachobjekten.

### 13.3 Dokumenttypen

Vorgesehene Dokumenttypen:

- Tankquittung,
- Werkstattrechnung,
- TÜV-Bericht,
- Versicherungsdokument,
- Leasingvertrag,
- Kaufvertrag,
- Fahrzeugschein-Kopie,
- Schadenfoto,
- Wartungsnachweis,
- Steuerbescheid,
- Sonstiges.

### 13.4 Dokumentverknüpfungen

Ein Dokument kann verknüpft werden mit:

- Fahrzeug,
- Tankvorgang,
- Wartung/Reparatur,
- Fahrt,
- Vertrag,
- Versicherung,
- Frist,
- später Finance-Control-Buchung.

### 13.5 Hashprüfung

Beim Import wird der SHA256-Hash berechnet. Bei späterer Prüfung soll die Anwendung den Hash erneut berechnen und Abweichungen melden können.

### 13.6 Keine stille Überschreibung

Wird ein Dokument mit gleichem Namen importiert, darf es nicht still überschrieben werden. Die Anwendung soll einen eindeutigen Speicherdateinamen erzeugen und den Originaldateinamen separat speichern.

---

## 14. Verträge und wiederkehrende Kosten

### 14.1 Einordnung

Dieses Modul ist für V1 als einfache Vertrags- und Kostenübersicht sinnvoll, kann aber bei Zeitdruck reduziert werden. Es ist besonders wichtig für die spätere Integration mit SASD Finance Control.

### 14.2 Vertragsarten

Vorgesehene Vertragsarten:

- Versicherung,
- Leasing,
- Finanzierung,
- Wartungsvertrag,
- Schutzbrief,
- Tankkarte,
- Ladekarte,
- Garantieverlängerung,
- Steuer/Abgabe,
- Sonstiges.

### 14.3 Datenfelder

Ein Vertrag soll erfassen:

- Fahrzeug,
- Vertragstyp,
- Anbieter / Lieferant,
- Vertragsnummer,
- Startdatum,
- Enddatum,
- Kündigungsfrist,
- monatliche Kosten,
- jährliche Kosten,
- Zahlungsintervall,
- nächster Zahlungstermin,
- Dokumentverknüpfung,
- Notizen,
- Status: aktiv, gekündigt, abgelaufen, archiviert.

### 14.4 Erinnerungen

Aus Vertragsdaten sollen Erinnerungen entstehen können, zum Beispiel:

- Kündigungsfrist läuft ab,
- Versicherung erneuern,
- Leasingende,
- Garantieablauf.

---

## 15. Fristen und Erinnerungen

### 15.1 Ziel

Das System soll wichtige Fahrzeugtermine sichtbar machen, damit Wartungen, TÜV, Versicherungen und Vertragsfristen nicht vergessen werden.

### 15.2 Pflichtfunktionen V1

Eine Erinnerung soll erfassen:

- Fahrzeug optional,
- Bezug zu Wartung/Vertrag/Dokument optional,
- Titel,
- Beschreibung,
- Fälligkeitsdatum,
- Fälligkeit bei Kilometerstand optional,
- Priorität,
- Status: offen, erledigt, überfällig, archiviert,
- Wiederholung optional,
- Notizen.

### 15.3 Statuslogik

Das System soll Erinnerungen automatisch einstufen:

- offen,
- bald fällig,
- fällig,
- überfällig,
- erledigt.

Der Zeitraum für „bald fällig“ soll konfigurierbar sein, zum Beispiel 30 Tage oder 1.000 km.

---

## 16. Kosten und Auswertungen

### 16.1 Ziel

Die Anwendung soll nicht nur Daten sammeln, sondern Kosten transparent machen.

### 16.2 Pflichtreports V1

Folgende Auswertungen sollen vorgesehen werden:

- Gesamtkosten pro Fahrzeug,
- Kosten pro Monat,
- Kosten pro Jahr,
- Kraftstoffkosten,
- Wartungskosten,
- Reparaturkosten,
- Vertragskosten,
- Kosten pro Kilometer,
- Durchschnittsverbrauch,
- Verbrauchsentwicklung,
- teuerste Kostenkategorien,
- offene Belege oder fehlende Dokumente.

### 16.3 Filter

Reports sollen filterbar sein nach:

- Fahrzeug,
- Zeitraum,
- Kategorie,
- Kostenart,
- Lieferant/Werkstatt,
- privat/geschäftlich soweit relevant.

### 16.4 Export

Reports sollen mindestens als CSV und Markdown exportierbar sein. Später kann PDF ergänzt werden.

---

## 17. Lieferanten, Werkstätten und Tankstellen

### 17.1 Ziel

Wiederkehrende Geschäftspartner sollen nicht jedes Mal neu geschrieben werden müssen. Dieses Modul soll später mit dem Lieferantenmodul von SASD Finance Control zusammengeführt oder synchronisiert werden können.

### 17.2 Pflichtfunktionen V1

Ein einfacher Geschäftspartnerdatensatz soll enthalten:

- Name,
- Typ: Tankstelle, Werkstatt, Versicherung, Leasinggeber, Händler, sonstiger,
- Adresse optional,
- Kontakt optional,
- Website optional,
- Notizen,
- aktiv/inaktiv.

### 17.3 Spätere Integration

Langfristig soll geprüft werden, ob Vehicle Control ein eigenes Lieferantenmodul behält oder auf eine gemeinsame Supplier-Komponente aus SASD Finance Control zugreift.

---

## 18. Checklisten

### 18.1 Einordnung

Checklisten sind für V1 optional, aber als geplante V2-Funktion ausdrücklich vorzusehen.

### 18.2 Geplante Checklisten

- Abfahrtskontrolle,
- Fahrzeugübergabe,
- Fahrzeugrückgabe,
- Unfallaufnahme,
- Werkstattannahme,
- Reifenwechsel,
- Wintercheck,
- Urlaubsfahrt-Check,
- Gebrauchtwagenbesichtigung.

### 18.3 Datenmodell-Vorbereitung

Das System soll später Checklisten mit einzelnen Punkten, Status, Notizen, Bildern und Dokumentenverknüpfungen unterstützen können.

---

## 19. Importfunktionen

### 19.1 V1-Importe

Für V1 sollen einfache Importe vorgesehen werden:

- Dokumentimport per Dateiauswahl,
- CSV-Import für Tankdaten optional,
- CSV-Import für Fahrten optional.

### 19.2 Importregeln

Importierte Daten sollen validiert werden. Fehlerhafte Zeilen sollen nicht still verworfen werden. Der Benutzer soll eine Importzusammenfassung erhalten.

### 19.3 Keine direkte Manipulation importierter Originaldaten

Originaldateien sollen unverändert bleiben. Die Anwendung speichert importierte Inhalte strukturiert in der Datenbank und legt Dokumente im Dokumentenarchiv ab.

---

## 20. Exportfunktionen

### 20.1 Pflicht-Exporte V1

Die Anwendung soll exportieren können:

- Fahrzeugliste als CSV,
- Tankbuch als CSV,
- Wartungshistorie als CSV,
- Fahrten als CSV,
- Kostenreport als Markdown,
- Fahrzeugdossier als Markdown,
- Dokumentmanifest als JSON oder Markdown,
- Backup als ZIP.

### 20.2 Fahrzeugdossier

Ein Fahrzeugdossier soll alle wichtigen Informationen zu einem Fahrzeug zusammenfassen:

- Stammdaten,
- Tankstatistik,
- Wartungshistorie,
- offene Erinnerungen,
- Vertragsübersicht,
- verknüpfte Dokumente,
- Kostenübersicht.

### 20.3 Steuerberater-/Buchhaltungsmappe

Für spätere Versionen soll ein Exportpaket vorbereitet werden, das Belege, Kostenübersichten und Dokumentenmanifest für Buchhaltung oder Steuerberater bündelt.

---

## 21. Backup und Wiederherstellung

### 21.1 Ziel

Da Fahrzeug- und Belegdaten langfristig wichtig sind, muss die Anwendung früh eine robuste Sicherungsfunktion erhalten.

### 21.2 Pflichtfunktionen V1

Die Anwendung soll ein ZIP-Backup erzeugen können mit:

- SQLite-Datenbank,
- Dokumentenarchiv,
- Manifestdatei,
- Versionsinformationen,
- Erstellungsdatum,
- optional Hashliste.

### 21.3 Wiederherstellung

Eine Wiederherstellung aus Backup soll geplant werden. Für V1 kann eine einfache Import-/Restore-Funktion vorgesehen werden. Vor einer Wiederherstellung muss die Anwendung ein Sicherheitsbackup des aktuellen Standes erzeugen.

### 21.4 Backup-Hinweise

Nach erfolgreichem Backup soll der Speicherort angezeigt werden. Fehler beim Backup dürfen nicht still ignoriert werden.

---

## 22. Audit, Historie und Löschregeln

### 22.1 Ziel

Die Anwendung soll nachvollziehbar arbeiten. Besonders wichtig sind Änderungen an Fahrten, Tankvorgängen, Wartungen, Dokumenten und Kosten.

### 22.2 Audit-Grundlagen V1

Das System soll mindestens protokollieren:

- Anlage wichtiger Datensätze,
- Änderung wichtiger Datensätze,
- Archivierung,
- Dokumentimport,
- Hashprüfung,
- Backup-Erstellung,
- Restore-Vorgang.

### 22.3 Keine stillen Löschungen

Fachliche Datensätze sollen grundsätzlich archiviert statt gelöscht werden, sobald sie mit anderen Daten verknüpft sind. Harte Löschung ist nur für offensichtliche Fehleingaben ohne Abhängigkeiten und nach Bestätigung möglich.

### 22.4 Änderungsbegründung

Für kritische Änderungen soll eine optionale oder verpflichtende Änderungsbegründung vorgesehen werden, zum Beispiel bei Kilometerstandkorrekturen.

---

## 23. Suche und Filter

### 23.1 Pflichtfunktionen V1

Die Anwendung soll Such- und Filtermöglichkeiten bieten für:

- Fahrzeuge,
- Tankvorgänge,
- Fahrten,
- Wartungen,
- Dokumente,
- Erinnerungen,
- Lieferanten/Werkstätten.

### 23.2 Suchkriterien

Gesucht werden soll nach:

- Freitext,
- Kennzeichen,
- Fahrzeugname,
- Datum/Zeitraum,
- Kostenart,
- Dokumenttyp,
- Lieferant,
- Status,
- Fälligkeit.

---

## 24. Benutzeroberfläche

### 24.1 Grundprinzip

Die UI soll ruhig, technisch-professionell und klar sein. Sie soll sich an der SASD-Dokument- und Projektästhetik orientieren: übersichtlich, nicht verspielt, mit klarer Navigation und guter Lesbarkeit.

### 24.2 Hauptbereiche

Die Anwendung soll folgende Navigationsbereiche erhalten:

- Dashboard,
- Fahrzeuge,
- Fahrten,
- Tankbuch,
- Wartung/Reparatur,
- Dokumente,
- Erinnerungen,
- Kostenberichte,
- Einstellungen.

### 24.3 Dashboard

Das Dashboard soll anzeigen:

- aktive Fahrzeuge,
- offene Erinnerungen,
- überfällige Termine,
- letzte Tankungen,
- letzte Wartungen,
- Kosten aktueller Monat,
- Warnungen bei fehlenden Belegen.

### 24.4 Kontextmenüs und Doppelklick

Wie bei anderen SASD-Projekten sollen intuitive Aktionen unterstützt werden:

- Doppelklick auf Fahrzeug öffnet Details,
- Doppelklick auf Dokument öffnet Vorschau/Datei,
- rechte Maustaste zeigt passende Aktionen,
- Kontextmenüs für Fahrzeuge, Tankungen, Wartungen und Dokumente.

### 24.5 Eingabedialoge

Dialoge sollen klare Pflichtfelder, Validierungshinweise und Hilfetexte bieten. Fehlermeldungen sollen verständlich sein.

---

## 25. Dokumentvorschau und Dateizugriff

### 25.1 V1-Anforderung

Dokumente sollen aus der Anwendung heraus geöffnet werden können. Die Anwendung kann dafür den Standardviewer des Betriebssystems verwenden.

### 25.2 Spätere Erweiterung

Eine integrierte Vorschau für PDF und Bilder kann später ergänzt werden.

---

## 26. Einstellungen

### 26.1 Pflichtfunktionen V1

Einstellbar sein sollen:

- Datenbankpfad,
- Dokumentenarchivpfad,
- Backup-Pfad,
- Währung,
- Standard-Verbrauchseinheit,
- Warnschwellen für Erinnerungen,
- Belegpflicht ja/nein,
- Logging-Level,
- Exportpfad.

### 26.2 Sichere Defaults

Die Anwendung soll sinnvolle Standardwerte verwenden, damit sie ohne aufwendige Einrichtung nutzbar ist.

---

## 27. Technische Architektur

### 27.1 Zielarchitektur

Empfohlen wird eine mehrschichtige Architektur:

```text
Sasd.VehicleControl.sln
 ├── src/
 │   ├── Sasd.VehicleControl.App
 │   ├── Sasd.VehicleControl.Domain
 │   ├── Sasd.VehicleControl.Application
 │   ├── Sasd.VehicleControl.Infrastructure
 │   ├── Sasd.VehicleControl.Import
 │   └── Sasd.VehicleControl.Export
 └── tests/
     ├── Sasd.VehicleControl.Domain.Tests
     ├── Sasd.VehicleControl.Application.Tests
     └── Sasd.VehicleControl.Infrastructure.Tests
```

### 27.2 Domain-Schicht

Enthält:

- Entitäten,
- Value Objects,
- fachliche Regeln,
- einfache Domain-Validierungen,
- keine UI-Abhängigkeiten,
- keine Datenbankabhängigkeiten.

### 27.3 Application-Schicht

Enthält:

- Services,
- Use Cases,
- DTOs,
- Validierungsabläufe,
- Repository-Interfaces,
- Koordination von Domain und Infrastruktur.

### 27.4 Infrastructure-Schicht

Enthält:

- SQLite-Zugriff,
- Repository-Implementierungen,
- Dateispeicherung,
- Hashing,
- Backup,
- Konfiguration,
- Logging.

### 27.5 Import/Export-Schichten

Import und Export sollen getrennt bleiben, damit CSV-, Markdown-, JSON- und spätere PDF-/DATEV-nahe Exporte sauber ergänzt werden können.

---

## 28. Vorgeschlagenes Datenmodell

### 28.1 Kernentitäten

Vorgesehene Tabellen/Entitäten:

- Vehicles,
- Drivers,
- Trips,
- FuelEntries,
- MaintenanceRecords,
- Documents,
- DocumentLinks,
- Reminders,
- Vendors,
- VehicleContracts,
- AuditLogEntries,
- Settings.

### 28.2 Erweiterungsentitäten

Für spätere Versionen:

- TireSets,
- TireChanges,
- Checklists,
- ChecklistItems,
- VehicleImages,
- FinanceLinks,
- ImportBatches.

### 28.3 ID-Konzept

Alle fachlichen Entitäten sollen stabile IDs erhalten, bevorzugt GUIDs oder robuste lokale IDs. IDs dürfen sich durch Export/Import nicht unkontrolliert ändern.

### 28.4 Zeitstempel

Wichtige Tabellen erhalten:

- CreatedAt,
- UpdatedAt,
- ArchivedAt optional,
- IsArchived.

---

## 29. Validierungsregeln

### 29.1 Allgemein

- Pflichtfelder dürfen nicht leer sein.
- Geldbeträge dürfen nicht negativ sein, außer spezielle Korrekturbuchungen werden später eingeführt.
- Kilometerstände dürfen nicht negativ sein.
- Datumswerte müssen plausibel sein.
- Verknüpfte Fahrzeuge müssen existieren.

### 29.2 Tankvorgänge

- Liter muss größer 0 sein.
- Gesamtbetrag muss größer oder gleich 0 sein.
- Kilometerstand muss plausibel sein.
- Bei Verbrauchsberechnung müssen vorherige Tankdaten berücksichtigt werden.

### 29.3 Fahrten

- Endkilometer größer/gleich Startkilometer.
- Datum erforderlich.
- Zweck erforderlich bei geschäftlicher Fahrt.

### 29.4 Wartung/Reparatur

- Datum erforderlich.
- Fahrzeug erforderlich.
- Kosten optional, aber wenn vorhanden nicht negativ.
- Bei TÜV/AU sollte nächster Termin gesetzt werden können.

---

## 30. Logging

### 30.1 Ziel

Logging soll Fehlersuche und Nachvollziehbarkeit unterstützen, ohne sensible Daten unnötig offenzulegen.

### 30.2 Logging-Inhalte

Protokolliert werden sollen:

- Anwendungsstart,
- Anwendungsende,
- Ladefehler,
- Speicherfehler,
- Import-/Exportvorgänge,
- Backup/Restore,
- unerwartete Exceptions.

### 30.3 Keine sensiblen Inhalte im Log

Logs sollen keine vollständigen personenbezogenen Bewegungsprofile, keine geheimen Daten und keine unnötigen Dokumentinhalte enthalten.

---

## 31. Sicherheit und Datenschutz

### 31.1 Lokale Daten

Die Anwendung speichert lokal sensible Daten. Der Benutzer muss wissen, wo Datenbank und Dokumente liegen.

### 31.2 Datenschutzkritische Daten

Besonders sensibel sind:

- Fahrten,
- Start- und Zielorte,
- Fahrer,
- private Nutzung,
- Fahrzeugdokumente,
- Rechnungen.

### 31.3 V1-Maßnahmen

- keine Cloud-Pflicht,
- keine automatische Standortüberwachung,
- klare Datenpfade,
- Backup-Hinweise,
- Audit-Grundlagen,
- keine Passwörter im Klartext, falls später Benutzerverwaltung entsteht.

### 31.4 Spätere Maßnahmen

- Datenbankverschlüsselung,
- Benutzerrollen,
- Passwortschutz,
- Mandantenfähigkeit,
- Export mit Datenschutzfilter,
- Lösch- und Aufbewahrungskonzepte.

---

## 32. Integration mit SASD Finance Control

### 32.1 Ziel

SASD Vehicle Control soll zunächst eigenständig bleiben, aber auf spätere Integration vorbereitet werden.

### 32.2 Gemeinsame Konzepte

Gemeinsam nutzbar sind langfristig:

- Dokumentenarchiv,
- Lieferanten/Stammdaten,
- Verträge,
- Bankbuchungen,
- Kostenkategorien,
- Reports,
- Backup,
- Audit-Log.

### 32.3 Geplante Integrationsfälle

- Tankbeleg wird einer Bankbuchung zugeordnet.
- Werkstattrechnung wird einem Lieferanten und einer Zahlung zugeordnet.
- Fahrzeugkosten fließen in Finance-Control-Reports ein.
- Verträge werden im zentralen Vertragsmodul sichtbar.
- Dokumente werden in einem gemeinsamen Archiv nachweisbar.

### 32.4 Technische Integrationsstrategie

Für V1 soll keine harte Kopplung entstehen. Stattdessen sollen Exportformate und IDs so gestaltet werden, dass spätere Synchronisation möglich ist.

---

## 33. Qualitätsanforderungen

### 33.1 Robustheit

Die Anwendung darf bei fehlenden Dokumenten, ungültigen Eingaben oder beschädigten Importdateien nicht unkontrolliert abstürzen.

### 33.2 Verständlichkeit

Fehlermeldungen sollen konkrete Hinweise geben, zum Beispiel: „Der Kilometerstand darf nicht kleiner sein als der letzte bekannte Kilometerstand. Bitte prüfen oder Korrektur begründen.“

### 33.3 Testbarkeit

Fachlogik muss automatisiert testbar sein. Domain- und Application-Schicht dürfen nicht von der UI abhängen.

### 33.4 Performance

Für V1 genügt Performance für kleine bis mittlere Datenmengen. Zielgröße:

- bis 50 Fahrzeuge,
- bis 100.000 Fahrten,
- bis 100.000 Tank-/Wartungseinträge,
- mehrere tausend Dokumente.

---

## 34. Tests

### 34.1 Unit-Tests

Tests sollen vorgesehen werden für:

- Fahrzeugvalidierung,
- Kilometerstandsregeln,
- Tankberechnung,
- Verbrauchsberechnung,
- Wartungsfälligkeiten,
- Reminder-Status,
- Dokumenthashing,
- Archivierungsregeln,
- Exportlogik.

### 34.2 Integrationstests

Integrationstests sollen prüfen:

- SQLite-Repositories,
- Dokumentimport,
- Backup-Erstellung,
- Restore-Grundfunktion,
- CSV-Export,
- Markdown-Export.

### 34.3 Manuelle Tests

Manuell zu prüfen:

- Fahrzeug anlegen,
- Tankung erfassen,
- Beleg importieren,
- Wartung erfassen,
- Erinnerung anzeigen,
- Report exportieren,
- Backup erzeugen,
- Anwendung neu starten und Daten prüfen.

---

## 35. Roadmap

### 35.1 Phase 0 – Dokumentation und Repository

- README,
- Screenshot-Mockup,
- Lastenheft,
- Pflichtenheft,
- Datenmodell-Entwurf,
- Roadmap,
- GitHub-Repositorystruktur.

### 35.2 Phase 1 – Anwendungsschale

- .NET Solution,
- Logging,
- Konfiguration,
- Hauptfenster,
- Navigation,
- SQLite-Grundstruktur,
- Testprojekt.

### 35.3 Phase 2 – Fahrzeugverwaltung

- Fahrzeuge anlegen/bearbeiten/archivieren,
- Fahrzeugliste,
- Fahrzeugdetails,
- Validierung,
- Tests.

### 35.4 Phase 3 – Dokumentenarchiv

- Dokumentimport,
- SHA256-Hash,
- Dokumenttypen,
- Dokumentverknüpfung,
- Dokumentliste,
- Hashprüfung.

### 35.5 Phase 4 – Tankbuch

- Tankvorgänge erfassen,
- Belege verknüpfen,
- Verbrauchsberechnung,
- Tankhistorie,
- Plausibilitätswarnungen.

### 35.6 Phase 5 – Wartung und Reparatur

- Wartungshistorie,
- Reparaturdatensätze,
- Werkstätten,
- Kosten,
- Folgetermine.

### 35.7 Phase 6 – Fahrten und Fahrer

- Fahrerverwaltung,
- Fahrten erfassen,
- Kilometerberechnung,
- Fahrtfilter,
- Export.

### 35.8 Phase 7 – Erinnerungen und Fristen

- Reminder-Service,
- Dashboard-Warnungen,
- Fälligkeiten nach Datum und Kilometerstand,
- Erledigt/Überfällig-Status.

### 35.9 Phase 8 – Kostenreports und Exporte

- Kostenübersicht,
- Fahrzeugdossier,
- CSV-Export,
- Markdown-Export,
- Dokumentmanifest.

### 35.10 Phase 9 – Backup und Audit

- ZIP-Backup,
- Restore-Grundlage,
- Audit-Log,
- Archivierungsregeln.

### 35.11 Phase 10 – Finance-Control-Vorbereitung

- Exportformate für Finance Control,
- Lieferanten-Mapping,
- Beleg-Mapping,
- Kostenkategorien,
- Integrationsdokumentation.

---

## 36. Priorisierung V1

### 36.1 Muss-Funktionen

- Fahrzeugverwaltung,
- Tankbuch,
- Wartung/Reparatur,
- Dokumentenarchiv mit Hash,
- Erinnerungen,
- einfache Kostenreports,
- CSV-/Markdown-Export,
- ZIP-Backup,
- Audit-Grundlagen.

### 36.2 Soll-Funktionen

- Fahrtenbuch,
- Fahrerverwaltung,
- Lieferanten/Werkstätten,
- Vertragsübersicht,
- Fahrzeugdossier,
- Dokumentmanifest.

### 36.3 Kann-Funktionen

- Reifenverwaltung,
- Checklisten,
- OCR,
- mobile Belegerfassung,
- Finance-Control-Synchronisation,
- PDF-Export,
- integrierte Dokumentvorschau.

### 36.4 Nicht-V1

- GPS-Live-Tracking,
- OBD-II,
- automatische Fahrterkennung,
- Routenoptimierung,
- vollständige Cloud-/Multiuser-Plattform.

---

## 37. Akzeptanzkriterien für eine erste brauchbare Version

Eine erste brauchbare Version gilt als erreicht, wenn:

1. mindestens ein Fahrzeug angelegt werden kann,
2. Tankvorgänge mit Beleg erfasst werden können,
3. Wartungen/Reparaturen mit Rechnung erfasst werden können,
4. Dokumente mit SHA256-Hash gespeichert werden,
5. offene Erinnerungen angezeigt werden,
6. Kosten pro Fahrzeug angezeigt werden,
7. ein CSV-Export funktioniert,
8. ein Markdown-Fahrzeugdossier erzeugt werden kann,
9. ein ZIP-Backup erstellt werden kann,
10. zentrale Fachlogik durch Tests abgesichert ist.

---

## 38. Offene Entscheidungen

Folgende Punkte müssen später entschieden werden:

- WinForms oder WPF für die erste UI?
- Gemeinsame Komponentenbibliothek mit SASD Finance Control?
- SQLite pur, Entity Framework Core oder Dapper?
- GUIDs oder Long-IDs?
- Wie streng sollen Fahrten nachträglich sperrbar sein?
- Wann wird Finance-Control-Integration umgesetzt?
- Soll OCR lokal oder über externe Dienste erfolgen?
- Wird später eine mobile Weboberfläche ergänzt?

---

## 39. Empfehlung zur Projektorganisation

SASD Vehicle Control soll als eigenes GitHub-Repository geführt werden, zum Beispiel:

```text
SASD-Vehicle-Control
```

Das Projekt soll aber im README und in der Architektur klar als Schwesterprojekt von SASD Finance Control beschrieben werden.

Empfohlene Repository-Struktur:

```text
SASD-Vehicle-Control/
 ├── README.md
 ├── LICENSE
 ├── docs/
 │   ├── 010_Lastenheft.md
 │   ├── 020_Pflichtenheft.md
 │   ├── 030_Datenmodell.md
 │   ├── 040_UI_Konzept.md
 │   ├── 050_Roadmap.md
 │   └── adr/
 ├── assets/
 │   └── screenshots/
 ├── src/
 └── tests/
```

---

## 40. Schlussbewertung

SASD Vehicle Control sollte nicht als bloßes Tankbuch geplant werden. Der Mehrwert liegt in der Kombination aus Fahrzeugverwaltung, Kostenkontrolle, Belegdokumentation, Auditierbarkeit und späterer Finance-Control-Anbindung.

Die Anwendung soll klein genug starten, um realistisch umgesetzt zu werden, aber sauber genug geplant sein, um später nicht neu gebaut werden zu müssen. Die wichtigste strategische Entscheidung lautet daher:

> Eigenes Projekt, eigenes Repository, eigene Fachdomäne – aber mit gemeinsamer SASD-Architekturphilosophie und vorbereiteter Integration in SASD Finance Control.

Damit kann SASD Vehicle Control ein sinnvoller Baustein im geplanten SASD Business Control Ecosystem werden.

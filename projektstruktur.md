FS25 RP Fix1701

Projektübersicht

FS25 RP Fix1701 ist ein webbasiertes Verwaltungssystem für den Farming Simulator 25 Roleplay Server.

Die Anwendung besteht aus:

- GitHub Pages Weboberfläche
- Supabase Datenbank
- Supabase Edge Functions
- Telegram Bot Benachrichtigungssystem
- Automatischen Server- und Feldüberwachungen
- Auftrags- und Einsatzverwaltung
- Organisations- und Hofverwaltung

---

Repositories

Webseite

Repository:

FS25-RP-Fix1701

API / Automatisierungen

Repository:

FS25-api

---

Aktueller Status

Funktionsfähig

- Benutzerverwaltung
- Login
- Nachrichten
- Nachrichtenantworten
- Aufträge
- Auftragskommentare
- Telegram-Benachrichtigungen
- Telegram Queue
- Organisationsverwaltung
- Hofverwaltung
- Serverstatusanzeige
- Feldverwaltung
- Benachrichtigungssystem

Telegram

Telegram läuft vollständig über Supabase Edge Functions.

Make.com wird nicht mehr verwendet.

---

Datenbankstruktur

---

Users

Speichert alle Benutzer des Systems.

Spalte| Typ| Beschreibung
id| int8| Benutzer-ID
created_at| timestamptz| Erstellung
PSN-Username| text| Benutzername
Vorname| text| Vorname
Passwort| text| Passwort
Telegram_id| int8| Telegram-ID
Hof| text| Hofname
Hof_id| int8| Hof-ID
Admin| bool| Administrator
Aktiviert| bool| Aktiviert

Beziehungen

Hof_id → Hoefe.id

Beispiel

id| PSN-Username| Vorname| Hof| Hof_id| Telegram_id| Admin
1| Disti1701| Felix| BGA F&M| 1| 6694745579| TRUE
2| TestUser| Max| Gemeinde| 1| 123456789| FALSE

---

User_Organisationen

Verknüpft Benutzer mit Organisationen.

Spalte| Typ
id| int8
User_id| int8
Organisation_id| int8
Rolle| text
Aktiv| bool

Beziehungen

User_id → Users.id

Organisation_id → Organisationen.id

Beispiel

User_id| Organisation_id| Rolle
1| 1| EMPTY
1| 2| Mitglied
1| 3| Mitglied
1| 5| Bürgermeister

---

Organisationen

Spalte| Typ
id| int8
created_at| timestamptz
Name| text
Farbe| text

Standardorganisationen

id| Name| Farbe
1| Polizei| Blau
2| Feuerwehr| Rot
3| Rettung| Weiß
4| Bauhof| Gelb
5| Gemeinde| Orange
6| Förster| Braun

---

Hoefe

Speichert alle Höfe.

Spalte| Typ
id| int8
created_at| timestamptz
Name| text
Telegram_gruppe| text

Beispiel

id| Name
1| BGA F&M

---

Felder

Verwaltet alle Felder des Servers.

Spalte
id
created_at
Feldnummer
Hof_id
Fruchtart
Feldgroesse
Besitzer
Gepfluegt
Gegrubbert
Gesaet
Gesaet_am
Gewalzt
Gekalkt
Geduengt_1x
Geduengt_2x
Duengen_nötig
Unkraut
Wachstumsstufe
Erntebereit
Ernte_Benachrichtigt
Letzte_Aktion

---

Fruchtarten

Liste aller verfügbaren Fruchtarten.

Spalte
id
created_at
Name

---

Auftraege

Speichert sämtliche Aufträge und Einsätze.

Spalte
id
Erstellt_am
Vorlage_id
Titel
Beschreibung
Typ
Status
Erstellt_von
Angenommen_von
Belohnung
Erledigt_am
Sichtbarkeit
Hof
Organisation
Auftragstyp
Ziel_id

---

Auftragsvorlagen

Vorlagen für wiederkehrende Aufträge.

Spalte
id
Titel
Beschreibung
Typ
Belohnung
Organisation
Erstellt_von
Aktiv

---

Auftrag_kommentare

Kommentare zu Aufträgen.

Spalte
id
User_id
Username
Kommentar
Erstellt_am
Sichtbar_fuer

---

Einsatz_Organisationen

Zuordnung von Einsätzen zu Organisationen.

Spalte
id
Auftrag_id
Organisation_id

Beziehungen

Auftrag_id → Auftraege.id

Organisation_id → Organisationen.id

---

Angebote

Marktplatzangebote und Dienstleistungen.

Spalte
id
Titel
Kategorie
Inhalt
Einheit
Preis
Bestand
Hof_id
Aktiv

---

Nachrichten

Interne Nachrichten.

Spalte
id
Titel
Inhalt
Erstellt_von
Erstellt_am
Empfaenger_typ
Empfaenger_user_id
Empfaenger_hof_id

---

Nachrichten_Antworten

Antworten auf Nachrichten.

Spalte
Id
Nachricht_id
Antwort
Erstellt_von
User_id
Erstellt_am

---

Organisation_Nachrichten

Interne Organisationsnachrichten.

Spalte
id
Organisation_id
Titel
Nachricht
Erstellt_von
Erstellt_am
Wichtig
Aktiv

---

Benachrichtigungen

Systemweite Benachrichtigungen.

Spalte
id
Titel
Nachricht
Typ
Erstellt_am
User_id
Hof_id
Organisation_id
Auftrag_id
Gelesen
Erledigt
Archiviert
Telegram_gesendet

---

Telegram_Queue

Telegram-Warteschlange.

Alle automatischen Nachrichten werden zunächst hier gespeichert und anschließend von den Edge Functions versendet.

Spalte
id
Titel
Nachricht
Typ
User_id
Hof_id
Organisation_id
Chat_id
Gesendet
Erstellt_am
Status
Fehler

Statuswerte

- Offen
- Gesendet
- Fehler

Beziehungen

User_id → Users.id

Hof_id → Hoefe.id

Organisation_id → Organisationen.id

---

Passwort_Reset

Passwortanfragen.

Spalte
id
created_at
User_name
Spieler_name
Nachricht
Status
Bearbeitet_von

---

Registrierungen

Registrierungsanfragen neuer Benutzer.

Spalte
id
created_at
Username
Passwort
Spielername
Telegram
Hof_id
Status
Bearbeitet_von

Beziehungen

Hof_id → Hoefe.id

---

Einladungscodes

Einladungssystem.

Spalte
id
created_at
Code
Verwendet
Erstellt_von
Verwendet_von

---

Serverstatus

Aktueller Zustand des Servers.

Spalte
id
Spieler_online
Monat
Tag
Zeit
Server_online
Github_update

Verwendung

- Spieleranzahl
- Spielzeit
- Serverstatus
- Versionsanzeige

Beispiel

Spieler_online| Monat| Tag| Zeit| Server_online
0| Oktober| 2| 11:09| TRUE

---

Systemablauf Telegram

1. System erstellt Benachrichtigung
2. Eintrag wird in Telegram_Queue gespeichert
3. Edge Function liest offene Datensätze
4. Telegram Nachricht wird versendet
5. Status wird auf Gesendet gesetzt
6. Fehler werden im Feld Fehler gespeichert

---

Rollenmodell

Benutzer

- Normale Nutzer
- Hofmitglieder

Organisationsrollen

- Mitglied
- Bürgermeister
- Weitere Rollen je Organisation

Administrator

Admin = TRUE

Vollzugriff auf sämtliche Funktionen.

---

Verwendete Technologien

- HTML
- CSS
- JavaScript
- GitHub Pages
- Supabase
- PostgreSQL
- Supabase Edge Functions
- Telegram Bot API

---

Projektinhaber

FS25 RP Fix1701

Entwicklung und Verwaltung:
Disti1701
Felix

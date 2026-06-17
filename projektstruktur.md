FS25 RP Fix1701

Projektübersicht V3.0

FS25 RP Fix1701 ist ein webbasiertes Verwaltungs- und Organisationssystem für den Farming Simulator 25 Roleplay Server.

Die Plattform dient als zentrale Steuerung für:

- Benutzerverwaltung
- Hofverwaltung
- Organisationsverwaltung
- Feldverwaltung
- Marktplatz
- Rechnungswesen
- Auftrags- und Einsatzsystem
- Strafregister
- Benachrichtigungen
- Telegram-Integration
- Serverüberwachung

Die Anwendung besteht aus:

- GitHub Pages Frontend
- Supabase Datenbank
- PostgreSQL
- Supabase Edge Functions
- Telegram Bot API
- Automatisierten Hintergrunddiensten

---

Repositories

Weboberfläche

Repository:
FS25-RP-Fix1701

Backend / Automatisierungen

Repository:
FS25-api

---

Aktueller Entwicklungsstand

Fertiggestellt

- Benutzerverwaltung
- Registrierungssystem
- Login
- Passwort Reset
- Nachrichten
- Nachrichtenantworten
- Organisationsnachrichten
- Benachrichtigungen
- Telegram Queue
- Telegram Versand
- Organisationsverwaltung
- Hofverwaltung
- Feldverwaltung
- Fruchtartenverwaltung
- Aufträge
- Einsatzverwaltung
- Auftragskommentare
- Marktplatz
- Rechnungswesen
- Serverstatus
- Adminbereich
- Strafregister V3.0

In Entwicklung

- Neue Home-Seite
- Hofaktivitäten
- Fahrzeugverwaltung
- Erweiterte Feldautomatisierung

---

Datenbankmodule

Benutzer

- Users
- Registrierungen
- Passwort_Reset
- Einladungscodes

Organisationen

- Organisationen
- User_Organisationen
- Organisation_Nachrichten

Höfe

- Hoefe
- Hof_Lager
- Lagerbewegungen

Felder

- Felder
- Fruchtarten

Marktplatz

- Angebote

Aufträge

- Auftraege
- Auftragsvorlagen
- Auftrag_Kommentare
- Einsatz_Organisationen

Nachrichten

- Nachrichten
- Nachrichten_Antworten

Rechnungen

- Rechnungen

Strafregister

- Strafregister

Benachrichtigungen

- Benachrichtigungen
- Telegram_Queue

System

- Serverstatus

---

Strafregister V3.0

Funktionen

- Automatisches Aktenzeichen
- Bearbeitungsstatus
- Fahrverbote
- Geldstrafen
- Haftstrafen
- Ausschlüsse
- Platzverweise
- Verwarnpunkte
- Automatische Telegram Meldungen
- Archivierung
- Hofsicht
- Polizeisicht
- Administratorsicht

Aktenzeichenformat

POL-2026-0001
POL-2026-0002
POL-2026-0003

---

Hofverwaltung V3.0

Funktionen

- Lagerbestand
- Lagerbewegungen
- Produktverwaltung
- Angebotsverwaltung
- Marktplatzintegration
- Rechnungserstellung
- Automatische Rechnungsnummern
- Telegram Benachrichtigungen
- Hofbezogene Datenverwaltung

Rechnungsnummern

RE-2026-0001
RE-2026-0002
RE-2026-0003

---

Telegram System

Ablauf

1. System erstellt Benachrichtigung
2. Eintrag wird in Telegram_Queue gespeichert
3. Edge Function verarbeitet offene Einträge
4. Telegram Nachricht wird versendet
5. Status wird aktualisiert
6. Fehler werden protokolliert

Statuswerte

- Offen
- Gesendet
- Fehler

---

Rollenmodell

Benutzer

- Benutzer
- Hofmitglied

Organisationen

- Mitglied
- Organisationsrollen
- Bürgermeister
- Weitere Rollen

Polizei

- Strafregister
- Einsätze
- Organisationsfunktionen

Administrator

Admin = TRUE

Vollzugriff auf sämtliche Module.

---

Verwendete Technologien

Frontend

- HTML
- CSS
- JavaScript

Backend

- Supabase
- PostgreSQL
- Edge Functions

Integration

- Telegram Bot API

Hosting

- GitHub Pages

---

Projektinhaber

FS25 RP Fix1701

Entwicklung und Verwaltung

Felix Distler
Disti1701

# FS25 RP Fix1701 – Projektstruktur

## Projekt

Webapp für FS25 RP Fix1701 mit:
- GitHub Pages als Webseite
- Supabase als Datenbank
- Supabase Edge Functions für Telegram
- Telegram Bot für Benachrichtigungen

## Wichtige Repositories

### Webseite
Repository:
FS25-RP-Fix1701

### API / Workflows
Repository:
FS25-api

## Status

Telegram:
funktioniert ohne Make.com

Nachrichten:
anzeigen, erstellen und Empfänger auswählen funktioniert


## Supabase Tabellen

### Angebote
# Tabelle: Angebote

Speichert Verkaufs- und Dienstleistungsangebote eines Hofes.

| Spalte | Typ | Beschreibung |
|---------|---------|---------|
| id | int8 | Eindeutige Angebots-ID |
| Titel | text | Name des Angebots |
| Kategorie | text | Frucht oder Dienstleistung |
| Inhalt | int8 | Menge des Angebots |
| Einheit | text | Einheit (Liter, kg, Auftrag usw.) |
| Preis | int8 | Preis |
| Bestand | int8 | Verfügbare Menge |
| Hof_id | int8 | Zugehöriger Hof |
| Aktiv | bool | Angebot aktiv oder deaktiviert |


### Auftraege
# Tabelle: Auftraege

Speichert alle Einsatz-, Marktplatz- und Organisationsaufträge.

| Spalte | Typ | Beschreibung |
|---------|---------|---------|
| id | int8 | Eindeutige Auftrags-ID |
| Erstellt_am | timestamptz | Zeitpunkt der Erstellung |
| Vorlage_id | int8 | Verknüpfte Auftragsvorlage |
| Titel | text | Titel des Auftrags |
| Beschreibung | text | Detailbeschreibung |
| Typ | text | Einsatz, Marktplatz usw. |
| Status | text | Offen, Angenommen, Erledigt |
| Erstellt_von | text | Benutzername des Erstellers |
| Angenommen_von | text | Benutzername des Bearbeiters |
| Belohnung | int8 | Vergütung für den Auftrag |
| Erledigt_am | timestamptz | Zeitpunkt der Fertigstellung |
| Sichtbarkeit | text | organisation, öffentlich usw. |
| Hof | text | Zugehöriger Hof |
| Organisation | text | Zielorganisation |
| Auftragstyp | text | Interne Kategorie |
| Ziel_id | int8 | Zielobjekt-ID |


### Auftrag_kommentare
# Tabelle: Auftrag_kommentare

Speichert Kommentare zu Aufträgen.

| Spalte | Typ | Beschreibung |
|---------|---------|---------|
| id | int8 | Eindeutige Kommentar-ID |
| User_id | int8 | ID des Benutzers |
| Username | text | Benutzername des Verfassers |
| Kommentar | text | Kommentarinhalt |
| Erstellt_am | timestamptz | Erstellungszeitpunkt |
| Sichtbar_fuer | text | Wer den Kommentar sehen darf |

### Auftragsvorlagen
# Tabelle: Auftragsvorlagen

Vorlagen für wiederkehrende Aufträge.

| Spalte | Typ | Beschreibung |
|---------|---------|---------|
| id | int8 | Eindeutige Vorlagen-ID |
| Titel | text | Titel der Vorlage |
| Beschreibung | text | Standardbeschreibung |
| Typ | text | Art des Auftrags |
| Belohnung | int8 | Standardbelohnung |
| Organisation | text | Zugeordnete Organisation |
| Erstellt_von | text | Ersteller der Vorlage |
| Aktiv | bool | Vorlage aktiv/inaktiv |


### Benachrichtigungen
### Einladungscodes
### Einsatz_Organisationen
### Felder
### Fruchtarten
### Hoefe
### Hofmitglieder
### Mitglieder
### Nachrichten
### Nachrichten_antworten
### Organisation_nachrichten
### Organisationen
### Passwort_Reset
### Registrierungen
### Serverstatus
### Telegram_queue
### User_organisationen
### Users

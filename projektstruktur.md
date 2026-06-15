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
# Tabelle: Benachrichtigungen

Speichert System-, Einsatz-, Auftrags- und Marktplatzmeldungen.

| Spalte | Typ | Beschreibung |
|---------|---------|---------|
| id | int8 | Benachrichtigungs-ID |
| Titel | text | Kurzer Titel |
| Nachricht | text | Vollständiger Text |
| Typ | text | Auftrag, Einsatz, Marktplatz usw. |
| Erstellt_am | timestamptz | Erstellungszeit |
| User_id | int8 | Empfänger Benutzer |
| Hof_id | int8 | Empfänger Hof |
| Organisation_id | int8 | Empfänger Organisation |
| Auftrag_id | int8 | Zugehöriger Auftrag |
| Gelesen | bool | Bereits gelesen |
| Erledigt | bool | Aktion erledigt |
| Archiviert | bool | Archivstatus |
| Telegram_gesendet | bool | Telegram versendet |

### Einladungscodes
CREATE TABLE Einladungscodes (
    id BIGINT PRIMARY KEY,
    created_at TIMESTAMPTZ,
    Code TEXT,
    Verwendet BOOLEAN,
    Erstellt_von TEXT,
    Verwendet_von TEXT
);

### Einsatz_Organisationen
CREATE TABLE Einsatz_Organisationen (
    id BIGINT PRIMARY KEY,
    Auftrag_id BIGINT,
    Organisation_id BIGINT
);

### Felder
### Felder

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige Feld-ID |
| created_at | timestamptz | Erstellungsdatum des Datensatzes |
| Feldnummer | int8 | Nummer des Feldes |
| Hof_id | int8 | Zugehöriger Hof |
| Fruchtart | text | Angebaute Fruchtart |
| Feldgroesse | text | Größe des Feldes |
| Besitzer | text | Eigentümer des Feldes |
| Gepfluegt | bool | Feld wurde gepflügt |
| Gegrubbert | bool | Feld wurde gegrubbert |
| Gesaet | bool | Feld wurde eingesät |
| Gesaet_am | timestamptz | Zeitpunkt der Aussaat |
| Gewalzt | bool | Feld wurde gewalzt |
| Gekalkt | bool | Feld wurde gekalkt |
| Geduengt_1x | bool | Erste Düngung durchgeführt |
| Geduengt_2x | bool | Zweite Düngung durchgeführt |
| Duengen_nötig | bool | Düngung erforderlich |
| Unkraut | bool | Unkraut vorhanden |
| Wachstumsstufe | int8 | Aktuelle Wachstumsstufe |
| Erntebereit | bool | Feld ist erntereif |
| Ernte_Benachrichtigt | bool | Erntebenachrichtigung versendet |
| Letzte_Aktion | text | Zuletzt ausgeführte Feldarbeit |

### Beispiel

```json
{
  "id": 1,
  "Feldnummer": 1,
  "Hof_id": 1,
  "Fruchtart": "Gras",
  "Feldgroesse": "0.8",
  "Besitzer": "-",
  "Gepfluegt": false,
  "Gegrubbert": false,
  "Gesaet": false,
  "Gewalzt": false,
  "Gekalkt": false,
  "Geduengt_1x": false,
  "Geduengt_2x": false,
  "Duengen_nötig": false,
  "Unkraut": false,
  "Wachstumsstufe": 0,
  "Erntebereit": true,
  "Ernte_Benachrichtigt": true,
  "Letzte_Aktion": "Keine vorhanden"
}
```

### Fruchtarten
### Fruchtarten

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige ID der Fruchtart |
| created_at | timestamptz | Erstellungsdatum des Datensatzes |
| Name | text | Name der Fruchtart |

### Beispiel

```json
{
  "id": 1,
  "Name": "Weizen"
}
```

### Hoefe
### Hoefe

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige Hof-ID |
| created_at | timestamptz | Erstellungsdatum des Datensatzes |
| Name | text | Name des Hofes |
| Telegram_gruppe | text | Telegram-Gruppen-ID oder Gruppenname für Benachrichtigungen |

### Beispiel

```json
{
  "id": 1,
  "Name": "BGA F&M",
  "Telegram_gruppe": null
}
```

### Hofmitglieder

### Hofmitglieder

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige ID des Hofmitglieds |
| created_at | timestamptz | Erstellungsdatum des Datensatzes |
| Hof | text | Zugehöriger Hof |
| Username | text | Benutzername des Mitglieds |
| Vorname | text | Vorname des Mitglieds |
| Rolle | text | Rolle im Hof (z. B. Mitglied, Admin) |
| Admin | bool | Kennzeichnet, ob das Mitglied Administratorrechte besitzt |

### Beispiel

```json
{
  "id": 1,
  "Hof": "BGA F&M",
  "Username": "max.mustermann",
  "Vorname": "Max",
  "Rolle": "Mitglied",
  "Admin": false
}
```

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

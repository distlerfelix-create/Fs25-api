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

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige ID des Mitglieds |
| created_at | timestamptz | Erstellungsdatum des Datensatzes |
| Benutzername | text | Benutzername des Mitglieds |
| Hof_id | int8 | Zugeordneter Hof |
| Organisationen_id | int8 | Zugeordnete Organisation |
| Admin | bool | Kennzeichnet, ob das Mitglied Administratorrechte besitzt |

### Beispiel

```json
{
  "id": 1,
  "Benutzername": "max.mustermann",
  "Hof_id": 1,
  "Organisationen_id": 1,
  "Admin": false
}
```

### Nachrichten

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige ID der Nachricht |
| Titel | text | Titel der Nachricht |
| Inhalt | text | Inhalt der Nachricht |
| Erstellt_von | text | Benutzername des Erstellers |
| Erstellt_am | timestamptz | Erstellungsdatum und Uhrzeit |
| Empfaenger_typ | text | Typ des Empfängers (z. B. User, Hof, Organisation) |
| Empfaenger_user_id | int8 | ID des Empfänger-Benutzers |
| Empfaenger_hof_id | int8 | ID des Empfänger-Hofs |

### Beispiel

```json
{
  "id": 1,
  "Titel": "Wartungsarbeit",
  "Inhalt": "Diese Seite befindet sich im Aufbau",
  "Erstellt_von": "Disti1701",
  "Erstellt_am": "2026-06-12T02:08:00Z",
  "Empfaenger_typ": "User",
  "Empfaenger_user_id": 1,
  "Empfaenger_hof_id": null
}
```

### Nachrichten_Antworten

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| Id | int8 | Eindeutige ID der Antwort |
| Nachricht_id | int8 | Verknüpfte Nachrichten-ID |
| Antwort | text | Inhalt der Antwort |
| Erstellt_von | text | Benutzername des Verfassers |
| User_id | int8 | ID des antwortenden Benutzers |
| Erstellt_am | timestamptz | Erstellungsdatum und Uhrzeit |

### Beispiel

```json
{
  "Id": 8,
  "Nachricht_id": 2,
  "Antwort": "Antwort test",
  "Erstellt_von": "Disti1701",
  "User_id": 1,
  "Erstellt_am": "2026-06-15T10:54:33.440000+00:00"
}
```

### Organisation_Nachrichten

| Feld | Typ | Beschreibung |
|--------|------|-------------|
| id | int8 | Eindeutige ID der Organisationsnachricht |
| Organisation_id | int8 | Zugeordnete Organisations-ID |
| Titel | text | Titel der Nachricht |
| Nachricht | text | Inhalt der Nachricht |
| Erstellt_von | text | Benutzername des Erstellers |
| Erstellt_am | timestamptz | Erstellungsdatum und Uhrzeit |
| Wichtig | bool | Kennzeichnet wichtige Nachrichten |
| Aktiv | bool | Gibt an, ob die Nachricht aktiv ist |

### Beispiel

```json
{
  "id": 1,
  "Organisation_id": 1,
  "Titel": "Wichtige Mitteilung",
  "Nachricht": "Die Organisation trifft sich am Freitag um 18 Uhr.",
  "Erstellt_von": "Disti1701",
  "Erstellt_am": "2026-06-15T12:00:00Z",
  "Wichtig": true,
  "Aktiv": true
}
```

### Organisationen

| Spalte | Typ | Beschreibung |
|---|---|---|
| id | int8 | Eindeutige ID der Organisation |
| created_at | timestamptz | Zeitpunkt der Erstellung |
| Name | text | Name der Organisation |
| Farbe | text | Zugeordnete Farbe der Organisation |

Beispieldaten:

| id | Name | Farbe |
|---|---|---|
| 1 | Polizei | blau |
| 2 | Feuerwehr | rot |
| 3 | Rettung | weiß |
| 4 | Bauhof | gelb |
| 5 | Gemeinde | orange |
| 6 | Förster | braun |

### Passwort_Reset

| Spalte | Typ | Beschreibung |
|---|---|---|
| id | int8 | Eindeutige ID des Reset-Antrags |
| created_at | timestamptz | Zeitpunkt der Erstellung |
| User_name | text | Benutzername des betroffenen Accounts |
| Spieler_name | text | Zugehöriger Spielername |
| Nachricht | text | Nachricht bzw. Begründung der Anfrage |
| Status | text | Aktueller Bearbeitungsstatus |
| Bearbeitet_von | text | Benutzer, der die Anfrage bearbeitet hat |

Beispieldaten:

| id | User_name | Spieler_name | Nachricht | Status | Bearbeitet_von |
|---|---|---|---|---|---|
| 1 | Musteruser | Max Mustermann | Passwort vergessen | Offen | NULL |
| 2 | Testuser | Peter Beispiel | Account gesperrt | Erledigt | Admin01 |

### Registrierungen

| Spalte | Typ | Beschreibung |
|---------|------|-------------|
| id | int8 | Eindeutige ID der Registrierung |
| created_at | timestamptz | Zeitpunkt der Registrierung |
| Username | text | Gewählter Benutzername |
| Passwort | text | Vom Benutzer vergebenes Passwort (verschlüsselt speichern) |
| Spielername | text | Name des Spielers im Spiel |
| Telegram | text | Telegram-Benutzername oder Kontakt |
| Hof_id | int8 | Referenz auf den ausgewählten Hof |
| Status | text | Bearbeitungsstatus der Registrierung |
| Bearbeitet_von | text | Administrator, der die Registrierung bearbeitet hat |

#### Beziehungen

| Feld | Verknüpfung |
|--------|------------|
| Hof_id | → Organisationen.id |

#### Zweck

Die Tabelle **Registrierungen** speichert neue Registrierungsanfragen von Spielern. Nach der Registrierung kann ein Administrator die Anfrage prüfen, bearbeiten und den Status entsprechend aktualisieren.

#### Beispiel

| id | Username | Spielername | Telegram | Hof_id | Status | Bearbeitet_von |
|----|----------|------------|----------|---------|---------|----------------|
| 1 | testuser | Max_Muster | @maxmuster | 3 | Offen | NULL |
| 2 | feuerwehr01 | Peter_Test | @petertest | 2 | Genehmigt | Admin01 |
| 3 | polizei99 | Lisa_Beispiel | @lisabeispiel | 1 | Abgelehnt | Admin02 |

### Serverstatus

| Spalte | Typ | Beschreibung |
|---------|------|-------------|
| id | int8 | Eindeutige ID des Serverstatus-Eintrags |
| Spieler_online | int8 | Aktuell verbundene Spieler |
| Monat | text | Aktueller Monat im Spiel |
| Tag | int8 | Aktueller Spieltag |
| Zeit | text | Aktuelle Spielzeit |
| Server_online | bool | Status des Servers (TRUE = online, FALSE = offline) |
| Github_update | text | Zeitpunkt des letzten GitHub-Updates |

#### Beziehungen

Keine Fremdschlüssel vorhanden.

#### Zweck

Die Tabelle **Serverstatus** speichert den aktuellen Zustand des Spielservers. Sie dient zur Anzeige von Serverinformationen auf dem Dashboard oder im Webpanel und wird regelmäßig aktualisiert.

#### Beispiel

| id | Spieler_online | Monat | Tag | Zeit | Server_online | Github_update |
|----|---------------|--------|-----|-------|---------------|---------------|
| 1 | 24 | Oktober | 2 | 11:09 | TRUE | 11.06.2026 12:25 |

#### Verwendung

- Anzeige der aktuellen Spieleranzahl
- Anzeige der Spielzeit und des Spieldatums
- Überwachung der Serververfügbarkeit
- Anzeige des letzten GitHub-/Versionsupdates


### Telegram_Queue

| Spalte | Typ | Beschreibung |
|---------|------|-------------|
| id | int8 | Eindeutige ID des Telegram-Eintrags |
| Titel | text | Titel der Telegram-Benachrichtigung |
| Nachricht | text | Inhalt der Nachricht |
| Typ | text | Art der Nachricht (z. B. Feld, Auftrag, Einsatz, Test) |
| User_id | int8 | Referenz auf einen Benutzer |
| Hof_id | int8 | Referenz auf einen Hof |
| Organisation_id | int8 | Referenz auf eine Organisation |
| Chat_id | int8 | Telegram Chat-ID des Empfängers |
| Gesendet | bool | Versandstatus der Nachricht |
| Erstellt_am | timestamptz | Erstellungszeitpunkt |
| Status | text | Status der Verarbeitung (Offen, Gesendet, Fehler) |
| Fehler | text | Fehlermeldung beim Versand |

#### Beziehungen

| Spalte | Referenz |
|---------|----------|
| User_id | Registrierungen.id |
| Hof_id | Hoefe.id |
| Organisation_id | Organisationen.id |

#### Zweck

Die Tabelle **Telegram_Queue** dient als Nachrichtenwarteschlange für Telegram-Benachrichtigungen. Alle automatischen Meldungen werden zunächst hier gespeichert und anschließend vom Telegram-Service verarbeitet und versendet.

#### Beispiele

| Titel | Typ | Status |
|---------|------|--------|
| 🌾 Feld erntereif | Feld | Gesendet |
| ✅ Einsatz/Auftrag beendet | Auftrag | Gesendet |
| 🚨 Neuer Einsatz | Einsatz | Gesendet |
| Test an mich | Test | Offen |

#### Verwendung

- Versand von Telegram-Benachrichtigungen
- Warteschlange für ausstehende Nachrichten
- Fehlerprotokollierung beim Versand
- Zuordnung zu Benutzern, Höfen oder Organisationen
- Nachverfolgung des Versandstatus

### User_Organisationen

| Spalte | Typ | Beschreibung |
|---------|------|-------------|
| id | int8 | Eindeutige ID der Zuordnung |
| User_id | int8 | Zugeordneter Benutzer |
| Organisation_id | int8 | Zugeordnete Organisation |
| Rolle | text | Rolle des Benutzers innerhalb der Organisation |
| Aktiv | bool | Status der Mitgliedschaft (TRUE = aktiv, FALSE = inaktiv) |

#### Beziehungen

| Feld | Referenz |
|--------|-----------|
| User_id | → User.id |
| Organisation_id | → Organisationen.id |

#### Zweck

Die Tabelle **User_Organisationen** verwaltet die Mitgliedschaften von Benutzern in Organisationen. Über die gespeicherte Rolle werden Berechtigungen und Funktionen innerhalb der jeweiligen Organisation gesteuert.

#### Beispiel

| id | User_id | Organisation_id | Rolle | Aktiv |
|----|---------|-----------------|--------|--------|
| 1 | 1 | 1 | EMPTY | TRUE |
| 2 | 1 | 2 | Mitglied | TRUE |
| 3 | 1 | 3 | Mitglied | TRUE |
| 4 | 1 | 5 | Bürgermeister | TRUE |

#### Verwendung

- Organisationsmitgliedschaften verwalten
- Rollen und Rechte vergeben
- Organisationszugriffe steuern
- Organisationsinterne Funktionen freischalten
- Berechtigungsprüfung für Einsätze, Aufträge und Verwaltung

### Users

| Spalte | Typ | Beschreibung |
|---------|------|-------------|
| id | int8 | Eindeutige Benutzer-ID |
| created_at | timestamptz | Zeitpunkt der Benutzerregistrierung |
| PSN-Username | text | PlayStation Network Benutzername |
| Vorname | text | Vorname des Benutzers |
| Passwort | text | Benutzerpasswort |
| Telegram_id | int8 | Telegram-ID für Benachrichtigungen |
| Hof | text | Zugehöriger Hof / Betrieb |
| Hof_id | int8 | Zugehöriger Hof |
| Admin | bool | Administratorstatus |
| Aktiviert | bool | Status des Benutzerkontos (TRUE = aktiv) |

#### Beziehungen

| Feld | Referenz |
|--------|-----------|
| Hof_id | → Hoefe.id |

#### Zweck

Die Tabelle **Users** speichert alle registrierten Benutzer des Systems. Sie enthält die Anmeldedaten, Telegram-Verknüpfung, Hofzuordnung sowie Berechtigungen des jeweiligen Benutzers.

#### Beispiel

| id | PSN-Username | Vorname | Hof | Hof_id | Telegram_id | Admin | Aktiviert |
|----|-------------|----------|------|--------|-------------|--------|-----------|
| 1 | Disti1701 | Felix | BGA F&M | 1 | 6694745579 | TRUE | TRUE |
| 2 | TestUser | Max | Gemeinde | 1 | 123456789 | FALSE | TRUE |

#### Verwendung

- Benutzerverwaltung
- Anmeldung und Authentifizierung
- Telegram-Benachrichtigungen
- Hofzuordnung
- Rollen- und Rechteverwaltung
- Verknüpfung mit Organisationen, Einsätzen und Aufträgen

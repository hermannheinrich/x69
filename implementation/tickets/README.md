# Ticketablage

Alle Tickets werden unabhängig von der Nutzerrolle unter
`implementation/tickets/<TICKET-ID>/` abgelegt.

## Neues Ticket anlegen

1. Den Ordner `implementation/tickets/_template/` kopieren.
2. Die Kopie in `implementation/tickets/<TICKET-ID>/` umbenennen.
3. Platzhalter ersetzen und nicht benötigte optionale Dateien entfernen.
4. `requirements.md` fachlich pflegen und die technische Übergabe erst nach
	fachlicher Freigabe starten.

## Standarddateien

- `README.md` — Kurzbeschreibung und Status
- `jira.md` — Jira-Metadaten, Beschreibung und Verknüpfungen
- `progress.md` — laufender Fortschritt
- `requirements.md` — fachliche Anforderungen
- `analysis.md` — technische Analyse und betroffene Objekte

Optionale Dateien wie `design.md`, `objects.md`, `transport.md`, `tests.md` und
`review.md` werden nur bei Bedarf angelegt.

Das vollständige kopierbare Template liegt unter
`implementation/tickets/_template/`.

`requirements.md` ist für Developer-Agents schreibgeschützt. Technische Agents
dürfen Anforderungen lesen, aber nicht verändern. Sie pflegen technische
Analyse, Design, Objektlisten, Fortschritt, Tests und Reviews in den jeweils
dafür vorgesehenen Dateien.
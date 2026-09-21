# Project Workflow

> Startpunkt für den rollenübergreifenden Projektablauf. Jira ist das führende
> System für Status und Ticketmetadaten. Das Repository dokumentiert fachliche
> Anforderungen, technische Entscheidungen, Nachweise und Übergaben.

## Jira-Lifecycle

Der bevorzugte Ablauf orientiert sich an den Jira-Statuswerten des PVCS-Projekts:

```text
Program Backlog
      |
      v
Funnel
      |
      v
Implementation
      |
      v
Entwicklung fertiggestellt
      |
      v
In Review
      |
      v
Done
```

Mögliche alternative Übergänge:

```text
Funnel ----------------------> won't do
Implementation --------------> Funnel
In Review --------------------> Implementation
```

## Statusdefinitionen

| Status | Bedeutung | Hauptverantwortung |
|---|---|---|
| `Program Backlog` | Idee oder grobe Initiative | Product Management |
| `Funnel` | Fachliche Konkretisierung und Refinement | Business Analysis + Product Management |
| `Implementation` | Technische Umsetzung läuft | Developer |
| `Entwicklung fertiggestellt` | Technische Umsetzung abgeschlossen | Developer |
| `In Review` | Technische und fachliche Prüfung | Reviewer + Business Analysis |
| `Done` | Abnahme und Abschluss | Product Management / fachlicher Owner |
| `won't do` | Wird nicht umgesetzt | Product Management |

## Definition of Ready

Ein Ticket kann von `Funnel` nach `Implementation` wechseln, wenn:

- Jira-Key, Issue-Typ und Beschreibung vorhanden sind.
- Ziel / Use Case und Business-Kontext beschrieben sind.
- Scope und Out of Scope feststehen.
- Betroffene Rollen und Nutzergruppen bekannt sind.
- Abhängigkeiten, Annahmen und offene Fragen dokumentiert sind.
- Akzeptanzkriterien im Format **ANGENOMMEN / WENN / DANN** prüfbar formuliert sind.
- Jira- und Confluence-Referenzen vorhanden sind.
- Die fachliche Freigabe erfolgt ist.
- Ein Ticketordner aus `implementation/tickets/_template/` angelegt wurde.

## Definition of Done

Ein Ticket kann nach `Done` wechseln, wenn:

- Alle Akzeptanzkriterien erfüllt oder begründet abgenommen sind.
- Die technische Implementierung abgeschlossen ist.
- Syntaxprüfung und relevante Tests erfolgreich waren.
- Das Review abgeschlossen ist.
- Die fachliche Prüfung erfolgt ist.
- Dokumentation und Nachweise aktualisiert sind.
- Der Transport dokumentiert ist.
- Kein Agent einen Transport freigegeben hat.
- Offene Punkte ausdrücklich dokumentiert oder geschlossen sind.

## Pflichtdateien je Phase

| Phase | Relevante Dateien |
|---|---|
| `Funnel` | `README.md`, `jira.md`, `requirements.md`, `progress.md` |
| `Implementation` | `analysis.md`, `design.md`, `objects.md`, `transport.md`, `progress.md` |
| `Entwicklung fertiggestellt` | `tests.md`, `progress.md` |
| `In Review` | `review.md`, `tests.md`, `progress.md` |
| `Done` | alle relevanten Dateien vollständig |

Alle Dateien werden aus `implementation/tickets/_template/` erzeugt. Nicht
benötigte optionale Dateien dürfen entfernt werden.

## Übergaben

### Business Analysis an Developer

- Anforderungen und Scope sind freigegeben.
- Akzeptanzkriterien sind prüfbar.
- Fachliche Quellen und Entscheidungen sind verlinkt.
- Offene Fragen und Annahmen sind sichtbar.
- Der Developer liest `requirements.md`, ändert sie aber nicht.

### Developer an Review

- Geänderte Objekte und Transport sind dokumentiert.
- Syntaxprüfung, Aktivierung und Tests sind ausgeführt oder als nicht verfügbar
  gekennzeichnet.
- Technische Analyse und Design sind nachvollziehbar.
- Der Transport wurde nicht freigegeben.

### Review an fachlichen Owner

- Review-Ergebnis und Findings sind in `review.md` dokumentiert.
- Akzeptanzkriterien und Testergebnisse sind nachvollziehbar.
- Offene Punkte haben einen Verantwortlichen oder sind geschlossen.

## Statushistorie

`progress.md` dokumentiert jeden wesentlichen Statuswechsel:

```markdown
## Statushistorie

| Datum | Status | Verantwortlich | Begründung |
|---|---|---|---|
| <YYYY-MM-DD> | Funnel | <Rolle> | <Begründung> |
```

## Rücksprünge und Ausnahmen

- Bei unklaren Anforderungen geht das Ticket zurück nach `Funnel`.
- Bei Findings im Review geht das Ticket zurück nach `Implementation`.
- Bei fehlgeschlagenen Tests bleibt das Ticket in `Implementation` oder geht
  dorthin zurück.
- `won't do` erfordert eine dokumentierte Product-Management-Entscheidung.
- Abweichungen vom Ablauf werden in `progress.md` begründet.

## Noch zu entscheiden

Dieser Workflow ist ein Startpunkt. Offene Prozessentscheidungen sind:

- Wer `Done` formal bestätigt.
- Ob `Entwicklung fertiggestellt` und `In Review` zwingend getrennte Jira-Status
  bleiben.
- Welche zusätzlichen Product-Management-Freigaben erforderlich sind.
- Ob ein eigener Status für fachliche Abnahme benötigt wird.

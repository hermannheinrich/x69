# Integration-Developer-Regeln

Diese Regeldatei definiert den Scope der Rolle `Integration_developer`.

## Geltungsbereich

- Die Rolle arbeitet primär auf der SAP Integration Suite.
- Die lokalen ABAP-/SAP-Entwicklungsrichtlinien in
  `governance/development_rules.md` gelten nicht für Integration-Suite-
  Artefakte.
- Insbesondere gelten für Integration-Suite-Artefakte nicht automatisch die
  ABAP-Regeln zu Y*-Namespace, YCC-Paketen, ABAP-Syntax, ABAP Unit oder SAP-
  Transporten.
- Für SAP Integration Suite gelten die vom Projekt und der Plattform
  freigegebenen Entwicklungs-, Sicherheits-, Deployment- und Reviewprozesse.

## MCPs und Zugriff

- Die Rolle verwendet dieselben gemeinsamen MCPs wie Business Analysis:
  Jira, Confluence, Porsche Glossary, SAP Docs und SAP Notes.
- ARC-1 ist optional und ausschließlich read-only für SAP-Kontext, Suche und
  Diagnose.
- SAPWrite, SAPActivate und SAPTransport sind für die Rolle nicht erlaubt.
- Ein Integration-Suite-MCP ist in diesem Repository aktuell nicht
  konfiguriert. Plattformzugriff erfolgt über die vom Projekt bereitgestellten
  Werkzeuge.

## Ticket- und Schreibgrenzen

- Tickets liegen rollenunabhängig unter
  `implementation/tickets/<TICKET-ID>/`.
- `requirements.md` ist fachlich und wird von dieser Rolle gelesen, aber nicht
  geändert.
- Technische Integration-Suite-Dokumentation darf in `analysis.md`,
  `design.md`, `objects.md`, `tests.md`, `review.md` und geeigneten
  Fortschrittsabschnitten gepflegt werden.
- Governance-Dateien dürfen nicht durch Integration-Developer-Agents geändert
  werden.
- Jira- und Confluence-Änderungen erfolgen nur mit explizit freigegebenem
  Werkzeug und nach Prüfung des Zielobjekts.
- Confluence-Schreibzugriffe sind ausschließlich im PVCS-Space erlaubt:
  `https://skyway.porsche.com/confluence/spaces/PVCS/overview`.

## Sicherheit

- Keine PATs, Passwörter, Service Keys, OAuth-Secrets, Zertifikate oder
  persönliche Konfigurationspfade committen.
- Keine produktiven Payloads, personenbezogenen Daten oder Zugangsdaten in
  Ticketdateien dokumentieren.
- Plattformfreigaben und Deployments müssen über den vorgesehenen
  Integration-Suite-Prozess erfolgen.

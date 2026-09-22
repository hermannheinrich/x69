# Integration-Developer-Setup

Dieses Onboarding richtet die Rolle für SAP Integration Suite ein.

## Voraussetzungen

- VS Code mit GitHub Copilot und MCP-Unterstützung
- Zugriff auf die Porsche-Netzwerkumgebung beziehungsweise VPN
- Zugriff auf die projektseitig bereitgestellte SAP Integration Suite
- Lokale Installationen der gemeinsamen MCPs aus `mcps/`
- Persönliche Jira-/Confluence-PATs, falls die lokalen Dienste sie benötigen

## 1. Governance lesen

Vor dem ersten Ticket lesen:

- `governance/README.md`
- `governance/project_context.md`
- `governance/integration_developer_rules.md`
- `implementation/tickets/README.md`
- `implementation/tickets/_template/`

## 2. Gemeinsame MCPs einrichten

Die Integration-Developer-Rolle verwendet dieselben gemeinsamen MCPs wie
Business Analysis. Richte sie über `mcps/README.md` und
`mcps/mcp.json.example` ein:

- Jira
- Confluence
- Porsche Glossary
- SAP Docs
- SAP Notes

## 3. Optionaler SAP-Kontext

Für read-only SAP-Recherche kann
`business_analyst/arc-1-readonly.example.json` verwendet werden. Die Vorlage
ist nicht für SAP-Änderungen, Aktivierungen oder Transporte freigegeben.

## 4. Integration Suite konfigurieren

Die Integration Suite ist derzeit nicht als MCP in diesem Repository
konfiguriert. Verwende ausschließlich den vom Projekt bereitgestellten Zugang,
die freigegebenen lokalen Werkzeuge und die zugehörigen Plattformprozesse.
Keine Zugangsdaten, Service Keys oder Zertifikate in dieses Repository eintragen.

## 5. Ticketarbeit

Tickets liegen unter:

```text
implementation/tickets/<TICKET-ID>/
```

Integration-Suite-Artefakte werden in den technischen Ticketdateien
`analysis.md`, `design.md`, `objects.md`, `tests.md` und `review.md`
dokumentiert. `requirements.md` ist fachlich und bleibt unverändert durch
technische Rollen.

Confluence darf ausschließlich im PVCS-Space beschrieben werden:

<https://skyway.porsche.com/confluence/spaces/PVCS/overview>

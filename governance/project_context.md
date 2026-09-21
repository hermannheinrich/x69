# Project Context

Diese Datei enthält nicht-geheime Projekt- und Integrationsparameter für das
Onboarding. Zugangsdaten, Tokens, Cookies und persönliche Pfade gehören nicht
hierher.

## Repository

- Projekt: iWAS Transformation / iWAS 3.0
- GitHub-Repository: `hermannheinrich/x69`
- Gemeinsame Ticketablage: `implementation/tickets/<TICKET-ID>/`
- Developer-Onboarding: `developer/setup.md`
- Gemeinsame MCP-Vorlagen: `mcps/`
- Verbindliche Regeln: `governance/development_rules.md`

## SAP E69

- Systemtyp: On-Premise
- SAP-URL: `https://e69.sap.porsche.biz`
- Mandant: `100`
- Sprache: `DE`
- ABAP-Release: `758`
- SAP-Zugriff: ARC-1 read-only für Business Analysts, read/write für Developer
- Erlaubte Custom-Pakete für ARC-1: `Y*`, `$TMP`
- Transportfreigaben durch Agents: verboten

## Gemeinsame MCPs

| Dienst | Lokaler Endpunkt |
|---|---|
| Jira | `http://127.0.0.1:8000/mcp` |
| Confluence | `http://127.0.0.1:8001/mcp` |
| Porsche Glossary | `http://127.0.0.1:8002/mcp` |
| SAP Docs | lokale stdio-Installation |
| SAP Notes | lokale stdio-Installation |

## Jira und Confluence

- Jira-Basis: `https://api.skyway.porsche.com/jira`
- Confluence-Basis: `https://api.skyway.porsche.com/confluence`
- Confluence-Projektbereich: `PVCS`
- Confluence-Projektbereich-URL: `https://skyway.porsche.com/confluence/spaces/PVCS/overview`
- PAT-Portal: `https://skyway.porsche.com/jira/plugins/servlet/desk/portal/1/create/9141`

PATs werden ausschließlich lokal in `.env`-Dateien verwaltet.

## Copilot

- Budgetverwaltung: `https://github.com/porsche-code/OctoFlowGitHubSelfServiceConsole`
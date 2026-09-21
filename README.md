# x69

## iWAS Transformation / iWAS 3.0

Dieses Repository ist der gemeinsame, rollenbasierte Einstiegspunkt für die
Entwicklung und Umsetzung rund um iWAS 3.0. Es bündelt Onboarding,
MCP-Setup-Vorlagen und später die für die jeweiligen Nutzergruppen relevanten
Agents.

## Nutzergruppen

- `developer/` — technische Entwicklung, insbesondere ABAP, CDS, RAP und Fiori
- `business_analyst/` — fachliche Analyse und Anforderungsarbeit
- `product_management/` — Produktsteuerung, Priorisierung und Roadmaps
- `implementation/` — gemeinsame Umsetzungsartefakte und Workflows

Die Developer-Agents liegen unter `developer/agents/` und werden beim
Developer-Onboarding mit eingerichtet. Die Agents für Business Analysis und
Product Management werden später ergänzt.

## Einstieg

1. Repository klonen und die passende Nutzergruppe öffnen.
2. Die zentrale MCP-Dokumentation unter `mcps/README.md` lesen.
3. Als Developer `developer/setup.md` vollständig ausführen; das installiert
	die Developer-Agents und richtet die MCPs ein.
4. Als Business Analyst `business_analyst/setup.md` vollständig ausführen.
5. `governance/README.md` und `governance/project_context.md` lesen.
6. `governance/project_workflow.md` für Status, Übergaben und Ticketphasen
	beachten.
7. Nur lokale `.env`-Dateien verwenden und niemals Zugangsdaten committen.

## MCPs

Die gemeinsamen MCP-Setup-Vorlagen liegen unter `mcps/`:

- Jira
- Confluence
- Porsche Glossary
- SAP Docs
- SAP Notes

ARC-1 ist bewusst nicht Teil der gemeinsamen Konfiguration. Developer nutzen
ARC-1 mit den erforderlichen Schreibrechten; Business Analysts können die
separate read-only Vorlage unter `business_analyst/` für SAP-Recherche nutzen.

Die Vorlagen enthalten keine produktiven Tokens, Passwörter, Cookies oder
Zertifikate. Jeder Nutzer muss seine lokalen Werte selbst eintragen.

## Zugangsdaten und Budget

- [Jira-/Confluence-PAT generieren](https://skyway.porsche.com/jira/plugins/servlet/desk/portal/1/create/9141)
- [Copilot-Budget erhöhen](https://github.com/porsche-code/OctoFlowGitHubSelfServiceConsole)

## Sicherheit

- Keine PATs, Passwörter, Cookies, Zertifikate oder lokalen `.env`-Dateien
	committen.
- Keine persönlichen absoluten Pfade in versionierte Konfigurationen schreiben.
- Interne MCP-Endpunkte nur in anonymisierten Templates dokumentieren.
- ARC-1-Schreibrechte und Transporte nur im Developer-Kontext verwenden.

## Status

Die Repository-Struktur, das gemeinsame MCP-Onboarding sowie Developer- und
Business-Analyst-Onboarding sind die erste Ausbaustufe. Product-Management-
Agents folgen in einem separaten Schritt.

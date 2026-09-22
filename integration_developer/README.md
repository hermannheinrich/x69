# Integration Developer

Dieser Bereich ist für Entwickler vorgesehen, die hauptsächlich auf der SAP
Integration Suite arbeiten.

## Zugriff

Die Rolle verwendet dieselben gemeinsamen MCPs wie Business Analysis:

- Jira
- Confluence
- Porsche Glossary
- SAP Docs
- SAP Notes
- optional ARC-1 read-only für SAP-Kontext

ARC-1 darf von dieser Rolle ausschließlich lesend für Kontext, Suche und
Diagnose verwendet werden. SAP-Objektänderungen, Aktivierungen und Transporte
sind nicht erlaubt.

## Integration Suite

Die konkrete Integration-Suite-Laufzeit und deren Werkzeuge werden außerhalb
dieses Repositorys bereitgestellt. Dieses Repository enthält aktuell keinen
separaten Integration-Suite-MCP.

Die lokalen ABAP-/SAP-Entwicklungsrichtlinien in
`governance/development_rules.md` gelten nicht für Integration-Suite-Artefakte.
Für Integration-Suite-Entwicklung gelten die vom Projekt beziehungsweise der
Plattform vorgegebenen Richtlinien und Freigabeprozesse.

## Einstieg

1. `setup.md` vollständig ausführen.
2. `governance/README.md`, `governance/project_context.md` und
   `governance/integration_developer_rules.md` lesen.
3. Die gemeinsamen MCPs über `mcps/` einrichten.
4. Integration-Suite-Zugriff und Plattformwerkzeuge gemäß der lokalen
   Projektbereitstellung konfigurieren.
5. Tickets unter `implementation/tickets/<TICKET-ID>/` bearbeiten.

Confluence-Schreibzugriffe sind ausschließlich im PVCS-Space zulässig:

<https://skyway.porsche.com/confluence/spaces/PVCS/overview>

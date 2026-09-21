# Business Analyst

Dieser Bereich bündelt fachliche Analysen, Anforderungen,
Prozessbeschreibungen und die dafür vorgesehenen Agents.

Der Einstieg erfolgt über [setup.md](setup.md). Business Analysts verwenden
die gemeinsamen Jira-, Confluence-, Glossary-, SAP-Docs- und SAP-Notes-MCPs.
ARC-1 kann zusätzlich über die read-only Vorlage für SAP-Recherche verwendet
werden. SAP-Schreibzugriffe gehören ausschließlich zum Developer-Setup.

Business Analysts pflegen die fachlichen Anforderungen in
`implementation/tickets/<TICKET-ID>/requirements.md`. Developer-Agents lesen
diese Datei, ändern sie aber nicht.

## BA-Agents

- `ba-lead.md` — koordiniert die fachliche Analyse und Übergabe
- `requirements-analyst.md` — pflegt Ziele, Scope und Akzeptanzkriterien
- `process-analyst.md` — beschreibt Ist-/Sollprozesse und Geschäftsregeln
- `ba-researcher.md` — recherchiert read-only in den verfügbaren Quellen

Die Agentdateien liegen unter `business_analyst/agents/` und werden über das
BA-Onboarding eingerichtet.

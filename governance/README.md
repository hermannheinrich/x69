# Governance

Dieser Ordner ist die zentrale Quelle für Regeln, Schreibrechte und
Projektkontext.

- [development_rules.md](development_rules.md) — verbindliche Entwicklungs-,
  Transport-, Test- und Artefaktregeln
- [project_context.md](project_context.md) — nicht-geheime Projektpfade,
  SAP-/MCP-Parameter und Jira-/Confluence-Kontext
- [project_workflow.md](project_workflow.md) — Jira-Lifecycle, Übergaben und
    Definition of Ready/Done
- [integration_developer_rules.md](integration_developer_rules.md) — Scope und
    Zugriffsgrenzen für die SAP Integration Suite

Die Ticketablage ist rollenunabhängig und liegt unter
`implementation/tickets/<TICKET-ID>/`. Die fachlichen Anforderungen in
`requirements.md` werden nicht von Developer-Agents verändert.

Developer-Agents dürfen Governance-Dateien nicht verändern. Änderungen an
Anforderungen erfolgen ausschließlich durch fachlich verantwortliche Rollen
oder nach expliziter Freigabe.

Die ABAP-/SAP-Entwicklungsrichtlinien gelten nicht für Integration-Suite-
Artefakte. Dafür gilt `integration_developer_rules.md`.
# Developer-Agents

Dieser Ordner enthält die Developer-Agents für das E69-Setup. Die Agents
bilden die Rollen und Zugriffgrenzen für die technische Entwicklung ab.

Die gemeinsamen Entwicklungsrichtlinien stehen in
`governance/development_rules.md`; der Projektkontext steht in
`governance/project_context.md`. Alle Developer-Agents beziehen sich auf diese
Dateien; rollenbezogene Regeln bleiben in den jeweiligen Agentdateien.

## Rollen

| Agent | Zweck | Zugriff |
|---|---|---|
| `senior-dev.md` | Planung, Delegation und Abschluss | delegiert an Spezialisten |
| `backend.md` | ABAP, CDS, RAP und Transporte | ARC-1, mit Schreibrechten |
| `frontend.md` | Fiori/UI5 und Metadaten | ARC-1 read-only, lokale Dateien |
| `reviewer.md` | Qualitäts- und Architekturprüfung | ARC-1 read-only/Diagnose |
| `legacy.md` | Recherche im Legacy-System | ARC-1 für E01, read-only |
| `skyway.md` | Jira- und Confluence-Recherche | `porsche-jira`, `porsche-confluence`, read-only |

## Zugriff und Grenzen

- Backend-Arbeiten verwenden ARC-1 mit den dafür erforderlichen Rechten.
- Frontend- und Review-Arbeiten verwenden ARC-1 nur lesend beziehungsweise
  diagnostisch.
- Der Legacy-Agent recherchiert ausschließlich im E01-Vergleichssystem.
- `skyway` liest Jira und Confluence über die gemeinsamen Porsche-MCPs.
- Ein Fiori-Deployment-MCP ist nicht eingerichtet; der Frontend-Agent nutzt
  deshalb nur die dokumentierten lokalen Werkzeuge und SAP-Metadaten.

## Nutzung und Installation

Die Installation ist Bestandteil von `developer/setup.md`. OpenCode verwendet
die Dateien als `.md`-Agents; VS Code erhält lokale `.agent.md`-Links auf die
versionierten Dateien. Dadurch bleibt das Repository die gemeinsame Quelle,
während beide lokalen Agentumgebungen dieselben Inhalte verwenden.

Nach der Installation VS Code beziehungsweise OpenCode neu laden. ARC-1
benötigt zusätzlich die lokale E69-MCP-Konfiguration aus
`developer/arc-1.example.json` und eine gültige SSO-Cookie-Session.

## Sicherheit

Keine Datei in diesem Ordner darf Tokens, PATs, Passwörter, SSO-Cookies,
Zertifikate oder persönliche absolute Pfade enthalten. Transporte dürfen von
keinem Agent automatisch freigegeben werden.

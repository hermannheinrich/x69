# Business-Analyst-Agents

Dieser Ordner enthält die fachlichen Agents für das PVCS-Projekt.

## Rollen

| Agent | Zweck | Schreibrechte |
|---|---|---|
| `ba-lead.md` | Koordiniert die fachliche Analyse und Übergabe | `requirements.md` und fachliche BA-Dokumentation |
| `requirements-analyst.md` | Formuliert Ziel, Scope und Akzeptanzkriterien | `requirements.md` und fachliche BA-Dokumentation |
| `process-analyst.md` | Beschreibt Ist-/Sollprozesse und Geschäftsregeln | fachliche Prozessdokumentation |
| `ba-researcher.md` | Recherchiert Quellen und liefert Befunde | read-only |

## Zugriff

- Jira, Confluence, Porsche Glossary, SAP Docs und SAP Notes dienen der
  Recherche und fachlichen Dokumentation.
- ARC-1 ist für BA-Agents ausschließlich read-only.
- SAP-Schreibzugriffe, Aktivierungen und Transporte sind nicht erlaubt.
- Confluence-Schreibzugriffe sind ausschließlich im PVCS-Space zulässig:
  <https://skyway.porsche.com/confluence/spaces/PVCS/overview>
- Governance-Dateien und technische Ticketdateien dürfen nicht verändert werden.
- Developer-Agents lesen `requirements.md`, ändern sie aber nicht.

## Ticketdateien

Die gemeinsame Ticketablage lautet:

```text
implementation/tickets/<TICKET-ID>/
```

BA-Agents arbeiten vor allem an:

- `jira.md`
- `requirements.md`
- fachlichen Teilen von `README.md`
- fachlichen Prozessdokumenten
- `progress.md` für fachliche Fortschritte

Technische Dateien wie `analysis.md`, `design.md`, `objects.md`,
`transport.md`, `tests.md` und `review.md` werden von den Developer-Agents
ergänzt und nicht fachlich überschrieben.

## Gemeinsame Regeln

Alle Agents folgen:

- `governance/development_rules.md`
- `governance/project_context.md`
- `governance/project_workflow.md`

## Installation

Die Installation ist Bestandteil des BA-Onboardings:

```bash
cd <REPOSITORY_ROOT>
for agent in ba-lead requirements-analyst process-analyst ba-researcher; do
  ln -sf "$PWD/business_analyst/agents/$agent.md" \
    "$HOME/Library/Application Support/Code/User/prompts/$agent.agent.md"
done
```

Die vollständige Einrichtung steht in [../setup.md](../setup.md). Nach der
Installation VS Code beziehungsweise OpenCode neu laden.

## Sicherheit

Keine Agentdatei darf PATs, Passwörter, Cookies, Zertifikate oder persönliche
absolute Pfade enthalten. Fachliche Anforderungen müssen aus Jira und
Confluence nachvollziehbar bleiben; Annahmen und offene Fragen sind explizit zu
dokumentieren.

# Business-Analyst-Setup

Dieses Dokument richtet den fachlichen Arbeitsbereich für Business Analysts im
Projekt iWAS 3.0 ein. Business Analysts arbeiten mit den gemeinsamen
Informations-MCPs und können ARC-1 optional read-only für SAP-Recherche nutzen.

Die BA-Agents liegen unter `business_analyst/agents/` und sind Bestandteil des
Onboardings.

## 1. BA-Agents installieren

### OpenCode

```bash
mkdir -p ~/.config/opencode/agents
for agent in ba-lead requirements-analyst process-analyst ba-researcher; do
	ln -sf "$PWD/business_analyst/agents/$agent.md" \
		"$HOME/.config/opencode/agents/$agent.md"
done
```

### VS Code und GitHub Copilot

```bash
mkdir -p "$HOME/Library/Application Support/Code/User/prompts"
for agent in ba-lead requirements-analyst process-analyst ba-researcher; do
	ln -sf "$PWD/business_analyst/agents/$agent.md" \
		"$HOME/Library/Application Support/Code/User/prompts/$agent.agent.md"
done
```

Nach der Installation VS Code beziehungsweise OpenCode neu laden.

## Voraussetzungen

- VS Code mit GitHub Copilot und MCP-Unterstützung
- Zugriff auf die Porsche-Netzwerkumgebung beziehungsweise VPN für Jira und Confluence
- Lokale Installationen der gemeinsamen MCPs aus `mcps/`
- Persönliche Jira-/Confluence-PATs, falls die lokalen Dienste sie benötigen

## 2. Governance lesen

Vor dem ersten Ticket die folgenden Dateien lesen:

- `governance/README.md`
- `governance/project_context.md`
- `governance/development_rules.md`
- `implementation/tickets/README.md`

Die gemeinsame Ticketablage ist:

```text
implementation/tickets/<TICKET-ID>/
```

## 3. Gemeinsame MCPs einrichten

Verwende die zentrale Anleitung unter `mcps/README.md` und die Beispiel-
Konfiguration `mcps/mcp.json.example`.

Für Business Analysts sind vorgesehen:

- Jira: Tickets, Status, Akzeptanzkriterien und Verknüpfungen
- Confluence: fachliche Dokumentation im PVCS-Projektbereich
- Porsche Glossary: Begriffe und Abkürzungen
- SAP Docs: fachliche und technische Referenzdokumentation
- SAP Notes: Recherche zu bekannten SAP-Hinweisen

ARC-1 ist nicht Bestandteil der gemeinsamen MCP-Konfiguration. SAP-
Objektänderungen, Aktivierungen und Transporte gehören weiterhin zum
Developer-Onboarding. Für read-only SAP-Recherche kann die Vorlage
`business_analyst/arc-1-readonly.example.json` lokal verwendet werden.

### ARC-1 read-only einrichten

1. Kopiere `business_analyst/arc-1-readonly.example.json` in deine lokale
	VS-Code-MCP-Konfiguration.
2. Ersetze `<HOME>` durch deinen lokalen Home-Pfad.
3. Stelle sicher, dass die E69-Cookie-Datei vorhanden und gültig ist.
4. Verwende ARC-1 ausschließlich für Lesen, Suche, Kontext und Diagnose.

Die Vorlage deaktiviert SAP-, Aktivierungs-, Transport-, Datenpreview-,
Freestyle-SQL- und Git-Schreibzugriffe. Bei `401` darf nur die Cookie-Session
erneuert werden; die Schreibschalter dürfen nicht aktiviert werden.

## 4. Ticketordner anlegen

Für ein neues Ticket den Ordner unter
`implementation/tickets/<TICKET-ID>/` anlegen. Die fachlichen Dateien sind:

```text
README.md
jira.md
requirements.md
progress.md
analysis.md
```

Business Analysts pflegen insbesondere `requirements.md` mit:

- fachlichem Ziel und Problemstellung
- Scope und Nicht-Scope
- Rollen und betroffenen Nutzergruppen
- Prozessbeschreibung und fachlichen Regeln
- Akzeptanzkriterien
- offenen Fragen und Annahmen
- Abhängigkeiten und relevanten Links

Technische Detaildateien wie `objects.md`, `transport.md`, `tests.md` und
`review.md` werden von den Developer-Agents ergänzt. Bestehende technische
Inhalte dürfen gelesen, aber nicht fachlich überschrieben werden.

## 5. Confluence-Schreibzugriff

Agents dürfen Confluence ausschließlich im PVCS-Projektbereich beschreiben:

<https://skyway.porsche.com/confluence/spaces/PVCS/overview>

Vor jedem Schreibzugriff muss der Ziel-Space geprüft werden. Persönliche,
fremde oder nicht eindeutig bestätigte Spaces sind nicht zulässig.

## 6. Jira und PATs

Jira und Confluence verwenden persönliche PATs. PATs dürfen nur in lokalen,
nicht versionierten `.env`-Dateien stehen.

PAT-Portal:

<https://skyway.porsche.com/jira/plugins/servlet/desk/portal/1/create/9141>

## 7. Fachlicher Übergang an Developer

Vor der technischen Umsetzung müssen mindestens folgende Punkte geklärt sein:

- Anforderungen verstanden und abgegrenzt
- Akzeptanzkriterien prüfbar formuliert
- relevante Jira- und Confluence-Links dokumentiert
- offene Fragen und Annahmen sichtbar
- betroffene Nutzergruppen und Prozesse beschrieben

Developer-Agents lesen `requirements.md`, ändern sie aber nicht. Änderungen an
fachlichen Anforderungen erfolgen durch Business Analysis oder Product
Management beziehungsweise nach expliziter fachlicher Freigabe.

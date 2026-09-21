# Developer-Setup

Dieses Dokument richtet die gemeinsamen MCPs und optional den Developer-only-MCP ARC-1 für E69 ein.

Die Developer-Agents in `developer/agents/` sind Bestandteil des Setups und
müssen vor der MCP-Konfiguration installiert werden.

## Voraussetzungen

- VS Code mit GitHub Copilot und MCP-Unterstützung
- Node.js 20 oder neuer für SAP Docs und SAP Notes
- Zugriff auf die Porsche-Netzwerkumgebung beziehungsweise VPN für Jira und Confluence
- Lokale Installationen von `mcp-sap-docs`, `sap-mcp-servers` und `mcporsche`
- Für ARC-1: gültige E69-SAP-Berechtigung und Zugriff auf den SSO-Cookie-Refresh

Die MCP-Serverquellen werden nicht durch dieses Repository installiert. Die
Pfade in den Templates müssen auf die lokale Installation angepasst werden.

## 1. Developer-Agents installieren

### OpenCode

OpenCode lädt Agents aus `~/.config/opencode/agents/`. Verlinke die
projektbezogenen Agentdateien dorthin:

```bash
mkdir -p ~/.config/opencode/agents
for agent in senior-dev backend frontend reviewer legacy skyway; do
   ln -sf "$PWD/developer/agents/$agent.md" \
      "$HOME/.config/opencode/agents/$agent.md"
done
```

### VS Code und GitHub Copilot

VS Code verwendet `.agent.md`-Dateien im User-Agentordner. Lege dort Links auf
die versionierten Agentdateien an:

```bash
mkdir -p "$HOME/Library/Application Support/Code/User/prompts"
for agent in senior-dev backend frontend reviewer legacy skyway; do
   ln -sf "$PWD/developer/agents/$agent.md" \
      "$HOME/Library/Application Support/Code/User/prompts/$agent.agent.md"
done
```

Nach der Installation VS Code beziehungsweise OpenCode neu laden. Die
fachlichen Inhalte bleiben im Repository; die Links machen sie in der lokalen
Agentauswahl verfügbar.

## 2. Gemeinsame MCPs konfigurieren

1. Öffne `mcps/mcp.json.example`.
2. Kopiere sie in deine VS-Code-MCP-Konfiguration.
3. Ersetze alle Platzhalter wie `<HOME>` und `<MCPORSCHE_DIR>` durch lokale
   Pfade.
4. Kopiere die benötigten Templates aus `mcps/env/` in die jeweiligen lokalen
   MCP-Verzeichnisse und benenne sie in `.env` um.
5. Trage PATs ausschließlich in diesen lokalen `.env`-Dateien ein.
6. Starte Jira, Confluence und Glossar über das vorhandene `mcporsche`
   Startverfahren.

Die gemeinsamen MCPs sind:

- Jira: `http://127.0.0.1:8000/mcp`
- Confluence: `http://127.0.0.1:8001/mcp`
- Porsche Glossary: `http://127.0.0.1:8002/mcp`
- SAP Docs: lokale Node-Ausführung
- SAP Notes: lokale Node-Ausführung

Details und Variablen stehen in `mcps/README.md`.

## 3. ARC-1 optional einrichten

ARC-1 ist ausschließlich für Developer vorgesehen. Verwende dafür die
anonymisierte Vorlage `developer/arc-1.example.json` und trage deine lokalen
Systemwerte nur in der nicht versionierten VS-Code-MCP-Konfiguration ein.

Benötigt werden:

- SAP-URL, Mandant, Sprache und ABAP-Release deines Zielsystems
- lokale CA-Chain als PEM-Datei, falls erforderlich
- lokale Netscape-Cookie-Datei für die SSO-Session
- `SAP_ALLOW_WRITES=true` nur bei bewusst benötigten Änderungen
- `SAP_DENY_ACTIONS=SAPTransport.release` immer beibehalten

### SAP-Session aktualisieren

Bei `401` oder `auth failure` den Cookie-Refresh ausführen:

```bash
~/Documents/Projekte/tools/sso-extractor/refresh-e69-cookies.sh
```

Danach im Browser anmelden und den Zugriff mit einem reinen Lesecheck
verifizieren. Cookie-Dateien niemals committen oder in Chat-Nachrichten teilen.

## 4. Verbindung prüfen

- Jira, Confluence und Glossary müssen auf den lokalen Ports erreichbar sein.
- SAP Docs und SAP Notes müssen ohne eingebettete Secrets starten.
- ARC-1 muss Discovery und einen sicheren Leseaufruf erfolgreich ausführen.
- Ein nicht erreichbarer Dienst ist ein Setup-Fehler, kein erfolgreicher Test.

## 5. Entwicklungsrichtlinien

Die verbindlichen Regeln für Namespace, YCC-Frameworks, Pakete, Transporte,
ABAP/CDS, Sicherheit, Tests, Ticketdokumentation und Reporting stehen in
`governance/development_rules.md`. Der Projektkontext steht in
`governance/project_context.md`. Alle Developer-Agents verwenden diese Dateien
als gemeinsame Grundlage.

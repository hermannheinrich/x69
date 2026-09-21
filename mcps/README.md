# Gemeinsame MCPs

Dieses Verzeichnis enthält portable Setup-Vorlagen für MCPs, die von allen
Nutzergruppen verwendet werden können.

## Enthaltene MCPs

| MCP | Transport | Lokaler Endpunkt bzw. Start |
|---|---|---|
| Jira | HTTP | `http://127.0.0.1:8000/mcp` |
| Confluence | HTTP | `http://127.0.0.1:8001/mcp` |
| Porsche Glossary | HTTP | `http://127.0.0.1:8002/mcp` |
| SAP Docs | stdio | lokale Node-Installation |
| SAP Notes | stdio | lokale Node-Installation |

ARC-1 ist absichtlich nicht in `mcp.json.example` enthalten. Der MCP wird
rollenbezogen eingerichtet:

- Developer verwenden `developer/arc-1.example.json` mit den erforderlichen
   Schreibmöglichkeiten.
- Business Analysts verwenden `business_analyst/arc-1-readonly.example.json`
   ausschließlich für SAP-Lesezugriffe.

## Einrichtung

1. Installiere oder klone die MCP-Server lokal entsprechend den internen
   Vorgaben.
2. Kopiere die passende `.env.example` in das jeweilige MCP-Verzeichnis und
   benenne sie in `.env` um.
3. Ersetze die Platzhalter durch deine lokalen Werte.
4. Starte Jira, Confluence und Glossary mit dem Startverfahren deiner lokalen
   `mcporsche`-Installation.
5. Kopiere `mcp.json.example` in deine lokale VS-Code-MCP-Konfiguration und
   passe die Pfade an.
6. Starte VS Code neu oder lade das Fenster neu.

## Environment-Templates

- `env/jira.env.example`
- `env/confluence.env.example`
- `env/glossary.env.example`
- `env/sap-notes.env.example`

Die Templates enthalten keine echten Werte. PATs, Passwörter, Cookies,
Zertifikate und persönliche Pfade bleiben außerhalb dieses Repositories.

## Sicherheitsregeln

- Niemals `.env`-Dateien mit echten Werten committen.
- Keine Tokens in `mcp.json`, README-Dateien, Logs oder Issues eintragen.
- Keine SSO-Cookies, `.pfx`-Dateien oder privaten Zertifikatsketten versionieren.
- Interne URLs in Templates durch Platzhalter ersetzen, falls sie nicht für
  das lokale Setup erforderlich sind.

## PATs

Für Jira und Confluence wird ein persönlicher PAT benötigt. Die Generierung
ist im internen Service-Portal möglich:

<https://skyway.porsche.com/jira/plugins/servlet/desk/portal/1/create/9141>

Der gemeinsame Confluence-Projektbereich ist:

<https://skyway.porsche.com/confluence/spaces/PVCS/overview>

Agents dürfen Confluence ausschließlich in diesem Bereich beschreiben. Vor
jedem Schreibzugriff muss der Ziel-Space geprüft werden.

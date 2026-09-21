# Development Rules

Diese Regeln gelten für alle Developer-Agents und SAP-Entwicklungsaufgaben im
E69-Kontext. Bei einem Konflikt mit einer konkreten Ticketanforderung muss der
Konflikt vor der Implementierung geklärt werden.

## SAP-Verbindung

- ARC-1 verwendet die lokale E69-SSO-Cookie-Jar.
- Bei `401` oder `auth failure` die Arbeit stoppen und den dokumentierten
  E69-Cookie-Refresh durchführen.
- Nach dem Refresh mit `SAPManage(action="probe")` prüfen, dass Such- und
  Transportzugriff verfügbar sind.
- Niemals Cookies, Tokens, Passwörter oder Zertifikatsinhalte anfordern,
  ausgeben oder committen.
- TLS-Prüfung nicht deaktivieren.

## Namespace und Pakete

- Für eigene Repository-Objekte ausschließlich den Y*-Namespace verwenden.
- Keine eigenen Z*-Objekte oder Objekte im SAP-Namespace anlegen oder ändern.
- Vor einer Eigenimplementierung vorhandene Frameworks und Utilities im Paket
  YCC prüfen.
- Neue Objekte dem passenden YCC-Unterpaket zuordnen, sofern das Ticket kein
  anderes Paket vorgibt.
- Produktive Objekte niemals `$TMP` zuordnen.
- Jedes produktive Objekt einem sauberen Paket und einem Transport zuordnen.
- Package-Interfaces verwenden, um öffentliche APIs klar zu begrenzen.

## Transporte

- Jedes Ticket und jede Aufgabe erhält einen eigenen Transportauftrag.
- Vor dem Anlegen eines Objekts nach einem passenden offenen Transport für das
  Ticket suchen.
- Falls kein passender Transport existiert, nach Analyse und Paketprüfung
  einen neuen Transport anlegen.
- Transporte niemals freigeben. Die Freigabe erfolgt ausschließlich durch den
  Benutzer.
- Geänderte Objekte und ihren Transport im Abschlussbericht nennen.

## ABAP und CDS

Die Porsche ABAP Programming Guidelines, Version 6.00.18, und modernes Clean
ABAP sind einzuhalten:

- Inline-Deklarationen und Konstruktor-Ausdrücke bevorzugen.
- Namenspräfixe verwenden: `lv_`, `lr_`, `ls_`, `lt_`, `lc_`, `<lfs_>`, `mv_`,
  `mr_`, `ms_`, `mt_`, `mc_` sowie typisierte Parameterpräfixe wie `iv_`,
  `ev_`, `is_`, `et_` und `rt_`.
- Veraltete Statements wie `MOVE`, `COMPUTE`, `REFRESH`, `FREE TABLE` und
  `OCCURS` nicht in neuem Code verwenden.
- `SELECT *` vermeiden; CDS-Views oder explizite Feldlisten verwenden.
- Keine `SELECT`-Statements in Schleifen.
- Klassenbasierte Exceptions verwenden.
- Sicheren dynamischen SQL-Code schreiben und unkontrollierte dynamische
  WHERE-Klauseln vermeiden.
- Sicherheitsrelevante Datenzugriffe mit `AUTHORITY-CHECK` absichern.
- Ausgaben gegen XSS schützen und veraltete Kryptografie wie MD5 oder DES
  nicht verwenden.
- Zwei Leerzeichen Einrückung, ABAP-Schlüsselwörter in Großschreibung und
  kurze zweckbezogene Kommentare auf Englisch verwenden.
- Keine Mandanten, Benutzernamen, Passwörter oder Systemparameter hardcodieren.

## Schreibrechte und Artefakte

- Confluence-Schreibzugriffe von Agents sind ausschließlich im Projektbereich
  `PVCS` erlaubt: `https://skyway.porsche.com/confluence/spaces/PVCS/overview`.
- Vor jedem Confluence-Write muss der Agent den Ziel-Space prüfen. Writes in
  persönlichen, fremden oder nicht eindeutig bestätigten Spaces sind verboten.
- Der aktuelle `skyway`-Agent bleibt standardmäßig read-only. Falls einem
  Agent später Confluence-Schreibwerkzeug freigegeben wird, gilt ausschließlich
  der `PVCS`-Bereich als erlaubtes Ziel.

- Die Schreibrechte der Developer-Rollen sind fachlich wie folgt begrenzt:

  | Agent | Darf schreiben | Darf nicht schreiben |
  |---|---|---|
  | `senior-dev` | nur nach Freigabe und im Rahmen der Orchestrierung | Anforderungen und Governance |
  | `backend` | technische Implementierung und technische Ticketdateien | `requirements.md`, Governance |
  | `frontend` | lokale UI5-/Fiori-Dateien und technische Ticketdateien | `requirements.md`, ABAP-Backend, Governance |
  | `reviewer` | nichts | SAP-Objekte, Ticketdateien, Anforderungen, Governance |
  | `legacy` | nichts | SAP-Objekte, Ticketdateien, Anforderungen, Governance |
  | `skyway` | nichts | Jira, Confluence, Ticketdateien, Anforderungen, Governance |
  | `business-analyst` | `requirements.md`, fachliche BA-Dokumentation und ARC-1-Lesezugriffe | SAP-Schreibzugriffe, Aktivierungen, Transporte, technische Implementierung, Governance |
  | `ba-lead` | `requirements.md` und fachliche BA-Dokumentation | technische Ticketdateien, SAP-Schreibzugriffe, Governance |
  | `requirements-analyst` | `requirements.md` und fachliche BA-Dokumentation | technische Ticketdateien, SAP, Governance |
  | `process-analyst` | fachliche Prozessdokumentation | technische Implementierung, SAP-Schreibzugriffe, Governance |
  | `ba-researcher` | nichts | alle Dateien, SAP-Schreibzugriffe, Jira-/Confluence-Schreibzugriffe |

- `implementation/tickets/<TICKET-ID>/requirements.md` ist ein fachliches
  Anforderungsartefakt und für Developer-Agents schreibgeschützt.
- Developer-Agents dürfen Anforderungen lesen, aber nicht ändern, ersetzen
  oder stillschweigend ergänzen.
- Änderungen an `requirements.md` erfolgen durch Business Analysis oder Product
  Management beziehungsweise nach expliziter fachlicher Freigabe.
- Developer-Agents dürfen technische Analyse, Design, Objektlisten,
  Fortschritt, Tests und Reviews in den dafür vorgesehenen Dateien pflegen.
- Governance-Regeln und Projektkontext sind schreibgeschützt für alle
  Developer-Agents.

Die fachliche Schreibsperre für `requirements.md` ist zusätzlich in den
jeweiligen Agentdefinitionen zu beachten. Wenn die technische Toolumgebung
keine pfadgenaue Sperre erzwingt, gilt diese Regel trotzdem verbindlich und
muss im Review geprüft werden.

## Tests und Validierung

- Bestehende Objekte vor Änderungen lesen und ihren Kontext prüfen.
- ABAP Unit für Kernlogik schreiben, wo es praktikabel ist.
- Lokale Testklassen `ltc_<objectname>` und Testmethoden
  `test_<what_is_tested>` nennen.
- Test-Doubles oder Fixtures verwenden, niemals Produktivdaten als Testdaten.
- Nach jedem Write Syntaxprüfung ausführen und relevante Befunde beheben.
- Geänderte Objekte aktivieren und fokussierte Tests ausführen.
- Nicht verfügbare Prüfungen ausdrücklich als nicht verfügbar melden, niemals
  als erfolgreich.

## Ticketdokumentation

Für jedes neue Ticket einen Ordner unter
`implementation/tickets/<TICKET-ID>/` anlegen. Mindestens enthalten sind:

- `README.md` mit Kurzbeschreibung und Status
- `jira.md` mit Jira-Metadaten, Beschreibung und Verknüpfungen
- `progress.md` mit laufendem Fortschritt
- `requirements.md` mit den fachlichen Anforderungen
- `analysis.md` mit betroffenen Objekten und YCC-Prüfung

Neue Ticketordner werden aus `implementation/tickets/_template/` erzeugt.

Bei Bedarf ergänzen:

- `design.md`
- `objects.md`
- `transport.md`
- `tests.md`
- `review.md`

## Reporting

Immer getrennt berichten:

- beobachtetes aktuelles Verhalten
- beabsichtigtes Verhalten
- geänderte Objekte
- Transport
- Syntaxprüfung, Aktivierung und Tests
- Review-Ergebnis
- offene Punkte oder nicht verfügbare Prüfungen
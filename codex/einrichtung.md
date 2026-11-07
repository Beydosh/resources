# Beydosh PIM mit Codex verbinden

Diese Anleitung ist für einen lokalen Codex-Chat unter Windows. Ein möglicher Auftrag lautet: **„Benutze mein Beydosh PIM. Richte die Verbindung ein und prüfe den Zugriff.“** Der Nutzer bestätigt die Zugriffsfrage im PIM.

## Einrichtung durch Codex

1. Prüfe die lokale Installation. Verwende den installierten Beydosh-Launcher unter `%LOCALAPPDATA%\Programs\Beydosh\Beydosh.Launcher.exe` oder den verifizierten Pfad der Beydosh-Installation. Bei Bedarf starte PIM über den normalen Launcher und warte, bis die Anwendung geöffnet und angemeldet ist. Die Anmeldung bleibt beim Nutzer.
2. Verwende den vorhandenen Server `beydosh_pim`, falls er auf diesen Launcher zeigt. Sonst starte den Launcher einmal mit `--mcp-stdio`, um die Werkzeuge abzufragen. `pim_request_access` muss in der Liste stehen. Fehlt es, braucht diese Installation ein PIM-Update. Frage den Zugriff einmal mit leeren Argumenten an. PIM zeigt **Zulassen** und **Abbrechen**. Warte auf das Ergebnis. Bei Ablehnung oder Abbruch endet die Einrichtung.
3. Nach `connected: true` registriere `beydosh_pim` in der lokalen MCP-Konfiguration. Erhalte alle vorhandenen Server und Einstellungen. Bei einem vorhandenen Eintrag mit abweichendem Ziel kläre den Konflikt, bevor du ihn änderst. Der Eintrag verwendet den tatsächlichen lokalen Pfad und sieht beispielsweise so aus.

   ```toml
   [mcp_servers.beydosh_pim]
   command = 'C:\Users\Beispiel\AppData\Local\Programs\Beydosh\Beydosh.Launcher.exe'
   args = ["--mcp-stdio"]
   default_tools_approval_mode = "writes"
   tool_timeout_sec = 90
   ```

4. Prüfe die Verbindung mit `pim_status`. Wenn der laufende Chat neue MCP-Server erst nach einem Neustart lädt, prüfe den Status über dieselbe lokale Launcher-Verbindung. Verwende den registrierten Server in Codex, sobald die Konfiguration geladen wurde.

Für einen einzelnen Aufruf über den Launcher werden pro Zeile JSON-RPC-Nachrichten geschrieben. Initialisiere die Verbindung, sende `notifications/initialized` und dann `tools/call` mit `params.name = "pim_request_access"` und `params.arguments = {}`. Die Antwort mit derselben ID enthält unter `result.structuredContent` das Ergebnis der Anfrage. Für `pim_status` gilt dasselbe Format.

## Was Codex danach tun kann

- Produkte suchen und Produktdaten, gespeicherte Preise, Märkte und Export-Verbindungen lesen.
- Produktänderungen oder Verkaufszustände zur Prüfung vorbereiten.
- Einen vorbereiteten Entwurf nach ausdrücklicher Bestätigung speichern. Für Veröffentlichung und Beendigung gelten die normalen PIM- und Plattformfreigaben.

Die Freigabe gilt für das angemeldete PIM-Konto und den aktuellen Arbeitsbereich auf diesem PC. Status, KI-Ressourcen und **Codex trennen** findest du unter **Einstellungen → KI & Automatisierung → Codex-Steuerung**. PIM muss für den Zugriff geöffnet bleiben. Diese Anleitung enthält öffentliche Informationen. Produktdaten, Zugangsdaten und die Zustimmung bleiben lokal.

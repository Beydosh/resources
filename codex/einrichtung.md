# Beydosh PIM mit Codex verbinden

Diese Anleitung gilt für einen lokalen Codex-Chat unter Windows. PIM muss geöffnet und angemeldet sein.

1. Verwende den in Codex eingerichteten Server `beydosh_pim`, wenn er auf den installierten Beydosh-Launcher zeigt. Der normale Pfad ist `%LOCALAPPDATA%\Programs\Beydosh\Beydosh.Launcher.exe` mit dem Argument `--mcp-stdio`.
2. Prüfe mit `pim_instance_status`, ob PIM läuft. Bei `running: true` verwende die laufende Instanz. Bei unklarem Status kläre zuerst den Zugriff. Ist PIM geschlossen, weise den Nutzer darauf hin.
3. Bei `access_required` und ausdrücklichem Auftrag rufe `pim_request_access` einmal auf. Der Nutzer entscheidet im geöffneten PIM selbst über **Zulassen** oder **Abbrechen**. Bei `sign_in_required` ist die persönliche Anmeldung erforderlich.
4. Prüfe mit `pim_status`, ob die Verbindung arbeitet. Verwende die zurückgegebene Arbeitsbereichskennung und prüfe, welche Werkzeuge dieser Adapter anbietet.

Der Status und **Codex-Zugriff entziehen** stehen unter **Einstellungen → KI & Automatisierung → Codex-Steuerung**. Die Freigabe ist an das Konto und den Arbeitsbereich gebunden. Ein Werkzeugaufruf darf keinen anderen Arbeitsbereich übernehmen.

Bei `pim_local_access_blocked` verwende die eingerichtete lokale Verbindung oder die vorgesehene Einzelfreigabe für den installierten Launcher. Der Nutzer entscheidet weiterhin im PIM. Bei `pim_unavailable` prüfe zuerst erneut `pim_instance_status`.

[Produkte paketweise bearbeiten](sammelbearbeitung.md) · [Updates und Fehler einordnen](status-und-fehler.md)

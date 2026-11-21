# Status, Updates und Fehler einordnen

- **PIM ist geöffnet, Codex erhält keine Antwort.** Prüfe `pim_instance_status`. Ein Zeitlimit allein ist kein Hinweis darauf, eine neue PIM-Instanz zu öffnen.
- **Ein Update wird angeboten.** Zeige die konkrete Version an und frage im Chat nach Zustimmung. Nutze `pim_request_update` mit genau dieser Version erst nach dem ausdrücklichen Ja. Die Anzeige im PIM bestätigt den Neustart. Prüfe danach `pim_status`.
- **Während eines Updates bricht die Verbindung ab.** Launcher-Wartung ab 0.9.154 kann laufende Codex-Adapter der betroffenen Installation schließen. Warte darauf, dass PIM wieder geöffnet ist. Prüfe danach Version und Zugriff. Wenn der Chat eine alte Werkzeugliste behält, stelle die lokale Verbindung neu her oder verwende einen neu verbundenen Chat.
- **Speichern antwortet verspätet oder unklar.** Prüfe den betroffenen Datensatz im PIM. Eine fehlende Antwort beweist keinen fehlgeschlagenen Schreibvorgang.
- **Der Katalogstand hat sich geändert.** Lade die betroffenen Datensätze neu und erstelle eine aktualisierte Vorschau. Die vorherige Bestätigung gilt für den ursprünglich geprüften Inhalt.
- **Das KI-Core-Raster fehlt.** In 0.9.153 und 0.9.154 ist die Platzierung im veröffentlichten Build fehlerhaft. Prüfe die Verbindung über den Status. Ein fehlendes Raster bedeutet für sich allein keinen Verbindungsfehler.

Für den sichtbaren PIM-Status kannst du mit `pim_set_activity` eine kurze sachliche Meldung zum aktuellen Schritt setzen. Verwende keine Zugangsdaten oder privaten Inhalte.

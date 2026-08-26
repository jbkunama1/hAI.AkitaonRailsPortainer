# AGENTS.md — hAI.AkitaonRailsPortainer

## Memory-Regeln (ai-memory)

Dieses Projekt nutzt ai-memory als Langzeitgedächtnis.

Nimm den MCP-Server
`https://haimcp.arbeitermili.eu/mcp/cms1vfcpi00042bs248msptyv`
(AnythingMCP, HTTPS) und führe dort die ai-memory-Tools aus.

### Zu Beginn einer Aufgabe

- Suche über den MCP-Server im Memory nach Einträgen zu diesem Projekt und
  den Themen "ai-memory", "Portainer", "9router" und "highfishNetwork".
- Nutze vorhandene Entscheidungen und Konventionen, statt neu zu raten.

### Während der Arbeit

- Speichere Architektur-Entscheidungen und gelöste Probleme sofort über den
  MCP-Server als Memory-Einträge (Typ: Decision / HowTo / Fact).
- Jeder Eintrag: Titel, Typ, Projekt, Datum, 3–8 kompakte Stichpunkte.

### Am Ende größerer Sessions

- Schreibe über den MCP-Server einen Handoff-Eintrag: aktueller Stand,
  getroffene Entscheidungen, offene Aufgaben, nächste Schritte.

## Projekt-Konventionen

- Deployment: Portainer-Stack aus diesem Repo (`docker-compose.yml`)
- Docker-Netzwerk: `highfishNetwork` (external, muss auf dem Host existieren)
- Image: `ghcr.io/jbkunama1/hai.akitaonrailsportainer:latest`
- Build: GitHub Actions, getriggert durch Tags `v*` oder manuell
  (workflow_dispatch)
- Zugriff auf ai-memory ausschließlich über den AnythingMCP-Server oben

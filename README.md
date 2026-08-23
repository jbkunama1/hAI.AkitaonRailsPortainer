# hAI.AkitaonRailsPortainer

ai-memory als Portainer-Stack und GHCR-Image für mein 9router-LLM-Setup.

- Upstream: https://github.com/akitaonrails/ai-memory
- Image: `ghcr.io/jbkunama1/hai.akitaonrailsportainer:latest`
- Zweck: Langzeit-Memory für Coding-Agents über HTTP

## Schnellstart

```bash
docker run -d --name ai-memory \
  --restart unless-stopped \
  -p 49374:49374 \
  -v ai-memory-data:/data \
  -e AI_MEMORY_AUTH_TOKEN=change-me \
  -e AI_MEMORY_ALLOWED_HOSTS=localhost,127.0.0.1,::1,host.docker.internal \
  ghcr.io/jbkunama1/hai.akitaonrailsportainer:latest
```

## Portainer Stack

1. Portainer öffnen → **Stacks** → **Add stack** → **Repository**
2. Repository-URL: `https://github.com/jbkunama1/hAI.AkitaonRailsPortainer.git`
3. Compose-Pfad: `docker-compose.yml`, Branch: `main`
4. Umgebungsvariablen setzen

Falls noch nicht vorhanden:

```bash
docker network create highfishNetwork
```

## Umgebungsvariablen

| Variable | Zweck |
|---|---|
| `AI_MEMORY_PORT` | Externer Port, Default `49374` |
| `TZ` | Zeitzone, Default `Europe/Berlin` |
| `AI_MEMORY_AUTH_TOKEN` | Bearer-Token für externe Zugriffe |
| `AI_MEMORY_ALLOWED_HOSTS` | Host-Allowlist, z. B. `192.168.178.10,localhost,127.0.0.1,host.docker.internal` |
| `AI_MEMORY_LLM_PROVIDER` | Optionaler LLM-Provider |
| `ANTHROPIC_API_KEY` | Optionaler Anthropic-Key |
| `OPENAI_API_KEY` | Optionaler OpenAI-Key |
| `AI_MEMORY_EMBEDDING_PROVIDER` | Optionaler Embedding-Provider |

## Beispiel für LAN-Zugriff

```env
AI_MEMORY_AUTH_TOKEN=dein-langes-zufaelliges-token
AI_MEMORY_ALLOWED_HOSTS=192.168.178.10,localhost,127.0.0.1,host.docker.internal
```

Danach ist der Dienst z. B. unter `http://192.168.178.10:49374` erreichbar.

Für API-/MCP-Zugriffe:

```http
Authorization: Bearer dein-langes-zufaelliges-token
```

## Build

Der Workflow baut bei Tags wie `v1.0.0` und manuell über **Run workflow**:

- `ghcr.io/jbkunama1/hai.akitaonrailsportainer:latest`
- `ghcr.io/jbkunama1/hai.akitaonrailsportainer:<tag>`

## Lizenz

MIT

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
  ghcr.io/jbkunama1/hai.akitaonrailsportainer:latest
```

## Portainer Stack

1. Portainer öffnen → **Stacks** → **Add stack** → **Repository**
2. Repository-URL: `https://github.com/jbkunama1/hAI.AkitaonRailsPortainer.git`
3. Compose-Pfad: `docker-compose.yml`, Branch: `main`
4. Optional: Umgebungsvariablen setzen

Falls noch nicht vorhanden:

```bash
docker network create highfishNetwork
```

## Umgebungsvariablen

| Variable | Zweck |
|---|---|
| `AI_MEMORY_PORT` | Externer Port, Default `49374` |
| `TZ` | Zeitzone, Default `Europe/Berlin` |
| `AI_MEMORY_LLM_PROVIDER` | Optionaler LLM-Provider |
| `ANTHROPIC_API_KEY` | Optionaler Anthropic-Key |
| `OPENAI_API_KEY` | Optionaler OpenAI-Key |
| `AI_MEMORY_EMBEDDING_PROVIDER` | Optionaler Embedding-Provider |

## Build

Der Workflow baut bei Tags wie `v1.0.0` und pusht nach GHCR:

- `ghcr.io/jbkunama1/hai.akitaonrailsportainer:latest`
- `ghcr.io/jbkunama1/hai.akitaonrailsportainer:<tag>`

## Lizenz

MIT

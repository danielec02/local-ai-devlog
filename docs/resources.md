# 📝 Log e Wiki Risorse - OpenClaw AI Setup

*Ultimo aggiornamento: 20 Aprile 2026*

In questo documento terrò traccia di tutta la documentazione, i paper e i video tutorial fondamentali per la costruzione, la sicurezza e l'evoluzione del mio assistente IA locale.

## 🦞 Progetto 1: Ecosistema OpenClaw (Focus Attuale)

### 🧠 Architettura Base e Componenti (Fase 1)
* **[OpenClaw Framework](https://openclaw.ai/):** Sito ufficiale e documentazione del framework che funge da gateway per l'agente.
* **[SearXNG (Integrazione OpenClaw)](https://docs.openclaw.ai/tools/searxng-search):** Documentazione specifica per collegare il motore di metaricerca all'agente tramite output JSON.
* **[Paper arXiv:2510.18921](https://arxiv.org/abs/2510.18921):** Studio di riferimento che conferma la validità del chip Apple Silicon (M1 e successivi) combinato col framework MLX come alternativa solida alle GPU nei data center per l'inferenza locale.

### 🎬 Setup Architettura e Sicurezza (Ispirazione: Bart Slodyczka)
Questi video costituiscono la base logica e pratica per l'isolamento dei componenti e il flusso di lavoro:
* **[OpenClaw Full Tutorial](https://www.youtube.com/watch?v=BoC5MY_7aDk&list=PLi7jtY2ZZqRYb7LXb50IjnsdmUOFq0fAW&index=5):** Base per l'installazione del gateway e collegamento con Telegram.
* **[Gemma 4 + SearXNG Private Setup](https://www.youtube.com/watch?v=T0CKsU0hQx4&list=PLi7jtY2ZZqRYb7LXb50IjnsdmUOFq0fAW):** Guida all'integrazione del motore IA con il web search in totale privacy.
* **[L'Architettura Docker (Metodo Bart)](https://www.youtube.com/watch?v=7ekNNMmiNrM&list=PLi7jtY2ZZqRYb7LXb50IjnsdmUOFq0fAW&index=6):** Il "Metodo Bart" per isolare il setup tramite Caddy, esponendo solo i webhook necessari.

### ⚙️ Automazione e Orchestrazione (n8n)
Risorse generiche raccolte per imparare a usare **n8n** per gestire i task ripetitivi e far comunicare in sicurezza i vari container Docker.

* **[Documentazione Ufficiale n8n](https://docs.n8n.io/):** Il punto di partenza è il "Beginner Course" per imparare le logiche, i nodi e i trigger.
* **[Canale YouTube n8n](https://www.youtube.com/@n8n-io):** Esempi pratici sulle automazioni drag-and-drop.
* **[Christian Lempa (YouTube)](https://www.youtube.com/@christianlempa):** Riferimento l'installazione pulita su Docker.

### 🔒 Sicurezza, Rete e Container
Risorse per sostituire il reverse proxy di Caddy e gestire i container in modo più sicuro sul Mac.
* **[Tailscale Documentation (Serve)](https://tailscale.com/kb/1242/tailscale-serve/):** Documentazione per esporre servizi localhost (come n8n) esclusivamente sulla propria rete VPN privata.
* **[Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/):** Da studiare in caso abbia la necessità assoluta di ricevere webhook esterni sicuri senza aprire porte sul router.
* **[Podman Rootless](https://github.com/containers/podman/blob/main/docs/tutorials/rootless_tutorial.md):** Alternativa a Docker Daemon per eseguire container senza privilegi di root.

---

## 💻 Progetto 2: Ecosistema Claude e IDE
Strumenti in fase di valutazione per un eventuale "pivot" del workflow di sviluppo.
* **[Claude Code (Documentation)](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview):** Lo strumento CLI ufficiale di Anthropic. *(Task: Verificare se la CLI supporta endpoint locali come Ollama o se è limitata alle API a pagamento).*
* **[Cursor IDE](https://www.cursor.com/):** Editor di codice forkato da VSCode e nativamente integrato con i modelli AI.
* **[Claude per VSCode](https://marketplace.visualstudio.com/items?itemName=Anthropic.claude-code):** Estensione ufficiale (alternativa a Cursor).

### 📓 Gestione della Conoscenza (PKM)
* **Obsidian:** (Aggiungere documentazione su come integrarlo con l'IA locale).
* **NotebookLM:** (Aggiungere documentazione su casi d'uso combinati).

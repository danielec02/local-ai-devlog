# 📝 Log e Wiki Risorse - OpenClaw AI Setup

*Ultimo aggiornamento: 14 Aprile 2026*

In questo documento terrò traccia di tutta la documentazione, i paper e i video tutorial fondamentali per la costruzione, la sicurezza e l'evoluzione del mio assistente IA locale.

### 🧠 Architettura Base e Componenti (Fase 1)
* **[OpenClaw Framework](https://openclaw.ai/):** Sito ufficiale e documentazione del framework che funge da gateway per l'agente.
* **[SearXNG (Integrazione OpenClaw)](https://docs.openclaw.ai/tools/searxng-search):** Documentazione specifica per collegare il motore di metaricerca all'agente tramite output JSON.
* **[Paper arXiv:2510.18921](https://arxiv.org/abs/2510.18921):** Studio di riferimento che conferma la validità del chip Apple Silicon (M1 e successivi) combinato col framework MLX come alternativa solida alle GPU nei data center per l'inferenza locale.

### 🎬 Setup Architettura e Sicurezza (Ispirazione: Bart Slodyczka)
Questi video costituiscono la base logica e pratica per l'isolamento dei componenti e il flusso di lavoro:
* **[OpenClaw Full Tutorial](https://www.youtube.com/watch?v=BoC5MY_7aDk&list=PLi7jtY2ZZqRYb7LXb50IjnsdmUOFq0fAW&index=5):** Base per l'installazione del gateway e collegamento con Telegram.
* **[Gemma 4 + SearXNG Private Setup](https://www.youtube.com/watch?v=T0CKsU0hQx4&list=PLi7jtY2ZZqRYb7LXb50IjnsdmUOFq0fAW):** Guida all'integrazione del motore IA con il web search in totale privacy.
* **[L'Architettura Docker Ultra-Sicura](https://www.youtube.com/watch?v=7ekNNMmiNrM&list=PLi7jtY2ZZqRYb7LXb50IjnsdmUOFq0fAW&index=6):** Il "Metodo Bart" per isolare il setup tramite Caddy, esponendo solo i webhook necessari.

---

### ⚙️ Automazione e Orchestrazione (Focus: n8n per la Fase 2)
Risorse raccolte per imparare a usare **n8n** per gestire i task ripetitivi e far comunicare in sicurezza i vari container Docker.

* **[Documentazione Ufficiale n8n](https://docs.n8n.io/):** Il punto di partenza ideale. Concentrarsi sulla sezione "Beginner Course" per imparare le logiche, i nodi e i trigger.
* **[Canale YouTube n8n](https://www.youtube.com/@n8n-io):** Ottimo per visualizzare i flussi di lavoro, con esempi pratici sulle automazioni drag-and-drop.
* **[Christian Lempa (YouTube)](https://www.youtube.com/@christianlempa):** Riferimento fondamentale per la parte sistemistica pura. Per capire come installare n8n in modo pulito su Docker e metterlo in sicurezza dietro un Reverse Proxy.

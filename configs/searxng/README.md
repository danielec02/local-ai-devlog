# 🔍 Configurazioni SearXNG
Per l'installazione e l'integrazione di SearXNG ho seguito la [documentazione ufficiale di OpenClaw](https://docs.openclaw.ai/tools/searxng-search).

### ⚠️ La mia modifica personalizzata
In questa cartella è salvato unicamente il mio file `settings.yml` modificato. 
La modifica fondamentale rispetto al file originale (come spiegato nella documentazione) riguarda l'abilitazione dell'output in formato JSON. Nello specifico, ho aggiunto `- json` sotto la voce `formats`, passaggio strettamente necessario per permettere all'agente IA di parsare i risultati della ricerca web.

### Setup
Avviare temporaneamente un container SearXNG per generare i file:
```bash
docker run -d -p 8888:8080 searxng/searxng
```

Una volta individuato il file `settings.yml` nella cartella `/etc/searxng`, sostituirlo con quello di questa cartella o semplicemente aggiungere `- json` sotto i `formats`.

Riavviare il container in modo da montare il file modificato.

### Configurazione finale
Una volta che il container è attivo (ed espone JSON sulla porta 8888), eseguire il comando:
```bash
openclaw configure --section web
```
e selezionare **"searxng"** come provider.

In alternativa, impostare la variabile d'ambiente per il riconoscimento automatico:
```bash
export SEARXNG_BASE_URL="http://localhost:8888"
```

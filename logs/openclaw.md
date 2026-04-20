# Phase 1 Log: Native Setup on Mac Mini

## [Ven 10 apr] - Preparazione Iniziale

- **Obiettivo:** Guardare i video di setup per capire l'architettura, scaricare il necessario e provare OpenClaw tramite Telegram (completare il setup, parlarci, verificare i file `.md` e assicurarsi che tutto sia a posto).
- **Risultato:** Raggiunto. Il Mac Mini era completamente pulito: ho disconnesso l'account iCloud e disattivato le password salvate. Ho scaricato Ollama, fatto il pull di `gemma4:e4b` (scelta dettata dai miei 16GB di RAM), impostato il bot Telegram, configurato API e token, e infine lanciato il comando di installazione di OpenClaw. Dopo vari tentativi, l'installazione è andata a buon fine.

- **Problemi riscontrati:**
  - **Setup macchinoso:** Tutto bene a parte l'installazione di OpenClaw, che ha richiesto diversi tentativi per capire le impostazioni e settarle correttamente. Penso di aver creato e cancellato vari file intermedi durante le prove, e ho il dubbio di non aver rimosso correttamente tutte le cartelle. Alla fine ci sono riuscito, non senza difficoltà.
  - **Latenza iniziale:** Le prime chat nella dashboard e tramite Telegram sono risultate un po' lente e l'agente non è riuscito a completare il security audit che gli avevo richiesto.

- **Prossimo test:** Capire meglio le logiche di funzionamento del sistema e implementare la ricerca web tramite SearXNG nell'apposito container Docker.

---

## [Lun 13 apr] - Setup Iniziale SearXNG e Test
- **Obiettivo:** Settare e utilizzare la dashboard di OpenClaw, il bot Telegram e SearXNG in locale. Poiché il pericolo numero 1 è l'accesso malevolo al bot, la priorità assoluta è la sicurezza. Effettuare prove e test generali del sistema.
- **Risultato:** Raggiunto. La struttura di base e la ricerca web funzionano, sebbene il sistema risulti un po' lento nelle comunicazioni.

- **Problemi riscontrati:**
  - **Latenza:** Latenza generale e difficoltà a comunicare in modo fluido tramite Telegram.
  - **Interruzioni Task:** Le operazioni o i comandi troppo lunghi si bloccano a metà e l'agente non continua ad aggiornarmi sullo stato di avanzamento.
  - **Iniziativa non richiesta:** Gli ho spiegato che *potevo* stoppare io momentaneamente il container di SearXNG per non far rilevare la porta web aperta durante l'audit. Ha frainteso e ha stoppato il container Docker da solo, senza che glielo avessi chiesto esplicitamente!
  - **Loop Logici:** La chat su Telegram ha portato diverse volte il bot a bloccarsi e rispondere con lo stesso identico messaggio a domande diverse (sembra che i problemi di "loop" nelle risposte siano tipici dei modelli più piccoli quando il contesto si riempie troppo).
  - **Gestione File:** Fa fatica a gestire e modificare i file di sistema. Non mi è ancora chiaro se questo avvenga per evitare danni (sicurezza), per qualche configurazione errata nei suoi file `.md`, o semplicemente per i limiti del modello stesso (Gemma4:e4b).

- **Prossimo test:** Effettuare un security audit completo e risolvere tutte le eventuali segnalazioni di vulnerabilità. Prendere ulteriore dimestichezza con le dinamiche e i limiti del sistema.

---

## [Lun 20 apr] - Riflessioni Architetturali e Alternative

Nessun test pratico sul sistema OpenClaw dall'ultimo aggiornamento.

- **Test Modelli Locali:** Ho scaricato `qwen3.5:9b` tramite Ollama. L'obiettivo a breve termine è testare le sue performance confrontandolo con `gemma4:e4b`, per capire quale si adatta meglio al ruolo di "cervello" mantenendosi stabile nei limiti dei miei 16GB di RAM.

Dopo essermi confrontato con persone più esperte, sono arrivato a rivalutare leggermente la roadmap futura. Chi mi ha dato questi consigli fa uso di Claude Code su sistema Linux e di altri tool molto interessanti per quanto riguarda la sicurezza dell'infrastruttura; in particolare mi è stato accennato l'utilizzo di Tailscale e Podman rootless. Mi sono stati raccomandati anche **Cursor** e la comoda implementazione ufficiale di Claude dentro VSCode.

Riflessioni e considerazioni raggiunte:

- **Networking e Sicurezza:**
Il motivo per cui Bart utilizza Caddy come "bodyguard" nel suo tutorial è perché lui esegue l'installazione su un server cloud DigitalOcean. Un server cloud è costantemente esposto all'internet pubblico (ha un IP pubblico), quindi usare un reverse proxy come Caddy per gestire l'HTTPS e bloccare le porte è obbligatorio.
Il mio caso è diverso: io sto usando un PC personale, già protetto dal NAT del router. Applicare la logica di Bart pari pari sul mio Mac Mini significherebbe dover aprire le porte del router domestico (Port Forwarding), introducendo inutili rischi di sicurezza.
Invece di usare Caddy, userò una combinazione tra la rete interna di Docker e Tailscale Serve (una funzione integrata in Tailscale).
  * **Comunicazione Interna (OpenClaw ↔ n8n):** OpenClaw e n8n comunicheranno tra loro esclusivamente tramite la rete invisibile interna di Docker.
  * **Interfaccia Utente (Io ↔ n8n):** L'interfaccia web di n8n non sarà esposta al mio Wi-Fi locale. Sarà legata solo al localhost del Mac. Tailscale prenderà quel localhost e lo esporrà in modo sicuro (e con HTTPS automatico) solo sulla mia rete privata Tailscale.

- **Nuovi task di studio aggiunti alla Roadmap:**
  - [ ] Studiare la documentazione di **Tailscale** e **Cloudflare Tunnels** (preparazione alla Fase 2 con n8n).
  - [ ] Documentarsi su **Podman rootless** (utilizzo al posto di Docker?).
  - [ ] Approfondire l'ecosistema Claude (**Claude Code**, **Claude Code CLI**, **Cursor**, estensione **VSCode**).
  - [ ] Analizzare l'integrazione di questi tool con **Obsidian** e **NotebookLM** per il PKM.

- **Decisione Attuale:**
Di fatto Claude Code andrebbe a sostituire il ruolo attuale di OpenClaw; questo però richiede un abbonamento o crediti API a consumo (a meno che effettivamente la versione CLI non offra la possibilità di utilizzare modelli in locale con Ollama). Dovendomi quindi prima informare su questo, al momento continuo i test di base con OpenClaw per mantenere il focus sull'ecosistema 100% gratuito, ma avvio ufficialmente la fase di documentazione per preparare il terreno a un "pivot" verso Claude.



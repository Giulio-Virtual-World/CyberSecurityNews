# 🚨 PHP2Shell, Node2Shell, HTTP2Shell: Settimana Critica per la Cybersecurity

Tra il **21 e il 23 ottobre 2026** sono state rese note tre vulnerabilità critiche che condividono un grave problema di gestione della memoria.

***

### 💡 Che cosa significa in parole semplici? (E qual è la portata?)
> Immaginate che il server di un sito web sia una cassaforte. Normalmente le applicazioni leggono e decomprimono i dati inviati dagli utenti (come file o richieste del browser) verificandone la dimensione. 
> 
> Con questi exploit, un malintenzionato può inviare un file o una richiesta appositamente "corrotta" o iper-compressa. Il software, nel tentativo di aprirla, subisce un errore di gestione della memoria. Questo non solo fa crollare il sistema (**crash**), ma permette all'attaccante di **eseguire comandi personali sul server a distanza (RCE)**, prendendone di fatto il controllo o rubando dati riservati presenti nella RAM.
> 
> **Perché la portata di questa crisi è colossale?**
> * **PHP (PHP2Shell):** PHP domina il web, alimentando circa il **70% di tutti i siti internet** con un linguaggio lato server noto (inclusi milioni di siti gestiti tramite WordPress, Joomla e Drupal).
> * **Node.js (Node2Shell):** È la tecnologia di backend scelta da quasi il **48% dei developer di tutto il mondo**, utilizzata per alimentare API e server di decine di milioni di servizi web e app enterprise.
> * **Brotli (HTTP2Shell):** Il formato di compressione Brotli è uno standard globale integrato nei browser moderni, nei server web (Nginx, Apache) e nelle principali CDN (Cloudflare, AWS). <u>Riguarda le fondamenta stesse della trasmissione del traffico dati di rete</u>.

***

## 🔴 PHP2Shell — `CVE-2026-109618` e `CVE-2026-109619`
<small>*(Reso noto il 21 Ottobre 2026)*</small>

Due vulnerabilità di corruzione della memoria nel core PHP, che possono causare crash e **Remote Code Execution (RCE)**. 
- **A rischio:** Tutti i server web e CMS come *WordPress*, *Drupal* e *Joomla* basati su PHP.
- 🛠️ **Versioni correttive:** `PHP 8.2.35`, `8.3.36`, `8.4.27` e `8.5.12` *(verificare anche le patch del proprio vendor)*.

***

## 🔴 Node2Shell — `CVE-2026-111497`
<small>*(Reso noto il 21 Ottobre 2026)*</small>

Un difetto nel decoder Brotli integrato in Node.js può provocare scritture fuori dai limiti della memoria (*out-of-bounds write*). 
- **Rischio:** Crash, leak di memoria e potenziale RCE durante l'elaborazione di dati compressi malevoli.
- 🛠️ **Versioni correttive:** `Node.js 22.23.4`, `24.22.1` e `26.12.1`.

***

## 🔴 HTTP2Shell — Ecosistema Brotli
<small>*(Emerso tra il 21 e il 24 Ottobre 2026)*</small>

Lo stesso problema si estende a librerie e runtime di terze parti (client HTTP, scraper, app Python o .NET). 
- **Vettori di attacco:** Un server malevolo può colpire un client che scarica dati; allo stesso tempo, un client malevolo può attaccare un server vulnerabile.
- 🛠️ **Versioni correttive:** `Brotli C-library 1.2.1` e `brotlicffi 1.2.1.0`.

***

### ⚠️ Cosa fare subito?

- [ ] **Aggiornare** immediatamente runtime (`PHP`, `Node.js`) e librerie vulnerabili.
- [ ] **Ricostruire e ridistribuire** le immagini Docker ed i container.
- [ ] **Analizzare i log** web/proxy per individuare anomalie o tentativi di exploit.
- [ ] **Attenzione:** Non considerare uno scanner privo di segnalazioni una garanzia assoluta (molte librerie Brotli sono incorporate direttamente nei binari e non sempre rilevate dagli scanner tradizionali).

> 📌 **Ricorda:** Non basta aggiornare il codice applicativo (es. il plugin WordPress o lo script Python). Bisogna aggiornare l'ambiente di esecuzione, il runtime e le dipendenze di basso livello!

`#CyberSecurity` `#PHP` `#NodeJS` `#Python` `#Brotli` `#DevSecOps` `#Docker` `#RCE`

<small>Report by: [www.giulio-virtual-world.com](https://www.giulio-virtual-world.com)</small>
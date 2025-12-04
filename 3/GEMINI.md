**PROMPT:**

Agisci come un istruttore esperto di **Cybersecurity, Malware Development e Sviluppo Backend**. Devi generare il contenuto testuale per una presentazione tecnica su "WordPress Internals & Security Architecture".

La presentazione è divisa in **5 Capitoli**. Per **OGNI CAPITOLO**, devi generare circa **8-10 slide distinte**, scendendo molto nel dettaglio tecnico. Evita slide riempitive; voglio contenuti densi e tecnici.

**Stile e Tono:**
* **Target:** Sviluppatori e studenti di security che conoscono già concetti base (es. Laravel, Linux).
* **Approccio:** "White Box". Spieghiamo come funziona il codice per capire come romperlo o difenderlo.
* **Confronti:** Usa spesso paragoni con Laravel/MVC per far capire le differenze architetturali.
* **Focus:** Per ogni componente, evidenzia sempre il risvolto di sicurezza (es. "Se questo file è scrivibile, succede X").

**Formato richiesto per ogni Slide:**
1.  **Slide ID:** (es. 1.1, 1.2...)
2.  **Titolo:** Tecnico e diretto.
3.  **Contenuto Visivo (Bullet Points):** 3-5 punti chiave, brevi, da mostrare a schermo. Includi snippet di codice PHP o path di file se rilevanti.
4.  **Speaker Notes (Script):** Un paragrafo discorsivo (100-150 parole) che il docente deve dire. Deve essere colloquiale ma molto tecnico, ricco di dettagli "internals" e scenari di attacco (Red Team).

---

**Struttura dei Capitoli da espandere:**

**CAPITOLO 1: Lo Stack LAMP e il Contesto di Esecuzione (Genera 8-10 Slide)**
* Espandi su: I componenti (Linux, Apache/Nginx, MySQL, PHP); Il ruolo dell'utente `www-data`; Differenza critica tra permessi Dev (777) e Prod (755/644); Il concetto di "Write Access = RCE" in PHP; Configurazione di Nginx/Apache per bloccare l'esecuzione PHP in cartelle specifiche; Versioni PHP e moduli pericolosi abilitati; Isolation (perché usare Docker/Chroot è meglio di un'installazione bare metal).

**CAPITOLO 2: Architettura Software - The "Event-Driven" Reality (Genera 8-10 Slide)**
* Espandi su: Perché WP non è MVC (niente rotte rigide); Il concetto di Event-Driven Architecture; Differenza tra `Actions` (fai qualcosa) e `Filters` (modifica dati); Esempi di codice per `add_action` vs `add_filter`; Come i plugin di sicurezza usano i Filters per sanitizzare; Come i malware usano le Actions per nascondersi o persistere; La "Global State" di WordPress (tutto è globale, rischi di contaminazione variabili); Confronto diretto con il Service Container di Laravel.

**CAPITOLO 3: Gerarchia del File System & Attack Surface (Genera 8-10 Slide)**
* Espandi su: Anatomia della root directory; Deep dive su `wp-config.php` (DB credentials, Salt Keys, Debug mode log leaks); La cartella `wp-content` come vettore principale; La cartella `uploads` e il problema delle Web Shell; `wp-includes` (il core intoccabile); File nascosti pericolosi (`.git`, `.env` lasciati per errore); File editing da Dashboard (`DISALLOW_FILE_EDIT`); Protezione tramite `.htaccess`.

**CAPITOLO 4: Database Schema & Critical Tables (Genera 8-10 Slide)**
* Espandi su: ER Diagram (schema a stella imperfetto); Focus su `wp_options` e il pericolo della row `siteurl`/`home`; La serializzazione dei dati PHP nel DB (e rischi di Object Injection); Tabella `wp_users` e struttura; Hashing delle password (`phpass`, MD5, Salt, iterazioni); Tabella `wp_usermeta` e la gestione dei ruoli (Capabilities) via stringhe serializzate; Privilege Escalation modificando il DB; Differenze con le Migration di Laravel.

**CAPITOLO 5: The Request Lifecycle (Genera 8-10 Slide)**
* Espandi su: Flusso di caricamento (`index.php` -> `wp-blog-header.php` -> `wp-load.php`); Inizializzazione del DB e dei Plugin; La Main Query (WP_Query); Template Hierarchy (spiegazione dettagliata della piramide di scelta template); Routing implicito vs Routing esplicito di Laravel; Il caricamento del WAF (quando avviene?); REST API Lifecycle (`wp-json`); XML-RPC Lifecycle; Come intercettare la request prima che venga renderizzata.

---

**Inizia ora a generare il contenuto completo seguendo questa struttura.**
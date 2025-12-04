### Metodo 1: Installazione Manuale (Step-by-Step)

Assicurati di sostituire la variabile `$DOWNLOAD_DIR`  con il percorso desiderato.

  * **Download del file di configurazione**
    Scarica il file `docker-compose.yml` nella directory di destinazione:

    ```bash
    curl -f -O -L https://greenbone.github.io/docs/latest/_static/docker-compose.yml --output-dir "$DOWNLOAD_DIR"
    ```


  * **Download delle immagini e avvio dei container**
    Esegui il pull delle immagini Docker e avvia i servizi in background (detached mode):

    ```bash
    docker compose -f $DOWNLOAD_DIR/docker-compose.yml pull
    docker compose -f $DOWNLOAD_DIR/docker-compose.yml up -d
    ```

  * **Monitoraggio dei log (Opzionale)**
    Per verificare che i servizi stiano partendo correttamente (utile per il debug iniziale):

    ```bash
    docker compose -f $DOWNLOAD_DIR/docker-compose.yml logs -f
    ```

    (Premi `Ctrl-C` per uscire).

  * **Cambio password Amministratore (Critico)**
    Il default è user: `admin`, password: `admin`. Per sicurezza, modificala immediatamente. Se usi caratteri speciali, racchiudi la password tra apici singoli:

    ```bash
    docker compose -f $DOWNLOAD_DIR/docker-compose.yml exec -u gvmd gvmd gvmd --user=admin --new-password='<TUA_PASSWORD>'
    ```

  * **Accesso all'interfaccia Web (GSA)**
    Una volta avviati i servizi e caricati i feed dei dati, accedi via browser:
    URL: `http://127.0.0.1:9392`

-----

### Metodo 2: Script Automatico

Questa procedura esegue automaticamente tutti i passaggi sopra descritti (download, setup e avvio) tramite uno script fornito ufficialmente (non l'ho testato).

  * **Esecuzione Script**
    Scarica, rendi eseguibile e lancia lo script di installazione:
    ```bash
    curl -f -O https://greenbone.github.io/docs/latest/_static/setup-and-start-greenbone-community-edition.sh && chmod u+x setup-and-start-greenbone-community-edition.sh
    ./setup-and-start-greenbone-community-edition.sh
    ```

**Nota tecnica:** Dopo l'avvio, OpenVAS impiegherà del tempo significativo per sincronizzare i feed delle vulnerabilità (NVT, SCAP, CERT). Fino al completamento del sync, i report delle scansioni potrebbero risultare incompleti.

------

### INSTALLARE METASPLOIT

Documentazione, sembra esserci anche la versione MacOS:
https://docs.metasploit.com/docs/using-metasploit/getting-started/nightly-installers.html

Alternativamente, ho trovato un'immagine docker:
https://hub.docker.com/r/metasploitframework/metasploit-framework/

da lanciare con shell interattiva sennò si blocca:
 docker run --rm -it metasploitframework/metasploit-framework:latest


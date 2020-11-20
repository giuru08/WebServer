# SERVER WEB SU VIRTUAL MACHINE CON APACHE2
### Rucco Giulio

## CONFIGURAZIONE
Installiamo **ssh** *apt-get install openssh-server*.<br>
Modifica dell'**indirizzo IP** tramite file presente in */etc/netplan/...*.<br>
**Comando** *netplan try*.<br>
Applicare la **modalità bridge** da VirtualBox.<br>
Installiamo il **webserver** *apt-get install apache2*.<br>
Si creano **più siti** sulla stessa macchina aggiungendo file di configurazione in */etc/apache2/sites-avaiable/...*.<br>
Dopo avr creato i flie in */etc/apache2/sites-avaiable/...* si **crea un nuovo sito con le configurazioni appena modificate** *a2ensite*.<br>
Installazione di programma **FTP** tramite comando *apt-get install vsftpd*.<br>
Modificare il **file di configurazione** */etc/vsftp.conf* come scritto su campus dal professore.<br>
Aggiungere 3 nuovi **utenti**, uno per ogni server *useradd -s /bin/bash -d /var/www/... -m nomeUtente*.<br>
Impostare la **password per ogni utente** *passwd nomeUtente* --> *Inserimento della password*.<br>
Dopo la creazione degli utenti si vanno a dare i **permessi alle cartelle** *chown -R nomeUtente:nomeUtente /var/www/cartellaSito*.<br>
Facendo così si potrà sia scaricare che caricare file sulla cartella in **FTP** da remoto sul desktop attraverso Filezilla.<br>

## CONTROLLI DI CONNESSIONE
- Si può verificare l'effettiva installazione di openssh provando a connettersi tramite "PuTTy" o da altre shell ssh.<br>
- Si può, inoltre, verificare quella di apache inserendo l'indirizzo IP della macchina virtuale nel browser e visualizzare la pagina default di apache in risposta.<br>
- Allo stesso modo, una volta creati i diversi siti tramite apache, basterà inserire il loro indirizzo nel browser per verificarne l'effettiva visualizzazione.<br>
- Si può, invece, verificare l'effettiva applicazione dell'indirizzo IP tramite i comandi ifconfig o ip addr.<br>
- Ora, si può verificare se la macchina è raggiungibile tramite comando *ping*.<br>
- Una volta modificato il file di configurazione per FTP si può verificare l'effettiva funzionalità provando a connettersi tramite *filezilla* o altri programmi che supportano FTP alla macchina virtuale.<br>
- Si prova prima di tutto la connessione, per vedere se è possibile accedere alla macchina, in seguito bisogna provare a passare un file dalla macchina virtuale al pc e, infine, dal pc alla macchina virtuale. Se tutti questi passaggi vanno a buon fine, possiamo dire di aver installato il client FPT con successo. <br>

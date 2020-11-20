# SERVER WEB SU VIRTUAL MACHINE CON APACHE2
### Rucco Giulio

## CONFIGURAZIONE
Installiamo **ssh** *apt-get install openssh-server*.<br>
Modifica dell'**indirizzo IP** tramite file presente in */etc/netplan/...*.<br>
**Comando** 
>*netplan try*
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

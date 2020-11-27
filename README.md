# SERVER WEB SU VIRTUAL MACHINE CON APACHE2
### Rucco Giulio

## CONFIGURAZIONE
Installiamo **ssh** 
>*apt-get install openssh-server*.<br>

Modifica dell'**indirizzo IP** tramite file presente in */etc/netplan/00-installer-config.yaml*.<br>
Esempio Configurazione:<br>
>
>
>     network:
>     version: 2
>     renderer: networkd
>     ethernets:
>       enp0s3:
>        # dhcp4: no
>         addresses: [172.16.29.121/16]
>         gateway4: 172.16.1.7
>         nameservers:
>             search: [virtual.marconi]
>             addresses: [172.16.1.18, 172.16.1.10]



**Comando** 
>*netplan try*

Esempio di risposta:
>
>
>Warning: Stopping systemd-networkd.service, but it can still be activated by:<br>
>  systemd-networkd.socket<br>
>Do you want to keep these settings?<br>
>Press ENTER before the timeout to accept the new configuration

Premere enter per accettare le configurazioni fatte.<br>
Applicare la **modalità bridge** da VirtualBox.<br>

## CHECKPOINT :white_check_mark:
Controlliamo sia in funzione con un ping a Google, con un ping dalla macchina fisica a quella virtuale o con il **comando**:
>*ip addr*

Esempio di **ping**: 
>*ping www.google.com*

o 

>*ping "IpDellaMAcchina"*

Installiamo il **webserver** 
>*apt-get install apache2*.<br>

Si creano **più siti** sulla stessa macchina aggiungendo file di configurazione in 
>*/etc/apache2/sites-avaiable/...*.<br>

Con il comando
>*cp 000-default.conf nomeFile.conf*

creiamo una copia del file di default su cui poi potremmo lavorare<br>
Esempio configurazione:<br>
>*ServerName sitoa-121.virtual.marconi<br>
ServerAdmin webmaster@localhost<br>
DocumentRoot /var/www/SitoA/webroot/*

Dopo avr creato i flie in */etc/apache2/sites-avaiable/...* si **crea un nuovo sito con le configurazioni appena modificate**
>*a2ensite*.<br>

Fatto questo si fa il reload di apache con questo comando<br>
>*systemctl reload apache2*

## CHECKPOINT :white_check_mark:
Si controlla con
>*netstat apache2*

se è attivo il servizio di apache2.<br>

Installazione di programma **FTP** tramite comando 
>*apt-get install vsftpd*.<br>

Modificare il **file di configurazione** 
>*/etc/vsftp.conf* 

come scritto su campus dal professore.<br>
Aggiungere nuovo **utente** 
>*useradd -s /bin/bash -d /var/www/... -m nomeUtente*.<br>

Impostare la **password per l'utente** 
>*passwd nomeUtente* --> *Inserimento della password*.<br>

Dopo la creazione dell' utente si vanno a dare i **permessi alle cartelle** 
>*chown -R nomeUtente:nomeUtente /var/www/cartellaSito*.<br>

## CHECKPOINT :white_check_mark:
Per controllare di avere creato in maniera adeguata l'utente si controlla accedendo da **PuTTY** con il *nomeUtente* e la *Password* corrispondente.

Facendo così si potrà sia scaricare che caricare file sulla cartella in **FTP** da remoto sul desktop attraverso Filezilla.<br>

# SERVER WEB SU VIRTUAL MACHINE CON APACHE2
### Rucco Giulio

## CONFIGURAZIONE
Installiamo **ssh** 
>*apt-get install openssh-server*.<br>

Modifica dell'**indirizzo IP** tramite file presente in */etc/netplan/00-installer-config.yaml*.<br>
Esempio Configurazione:<br>
>*# This is the network config written by 'subiquity'<br>
>
>   network:<br>
>
>     version: 2<br>
>
>     renderer: networkd<br>
>
>     ethernets:<br>
>
>       enp0s3:<br>
>
>        # dhcp4: no<br>
>
>         addresses: [172.16.29.121/16]<br>
>
>         gateway4: 172.16.1.7<br>
>
>         nameservers:<br>
>
>             search: [virtual.marconi]<br>
>
>             addresses: [172.16.1.18, 172.16.1.10]*<br>



**Comando** 
>*netplan try*

Premere enter per accettare le configurazioni fatte.<br>
Applicare la **modalità bridge** da VirtualBox.<br>

## CHECKPOINT :white_check_mark:
Controlliamo sia apposto con un ping a Google o un ping dalla macchina fisica a quella virtuale.
>*ping www.google.com*

o 
>*ping "IpDellaMAcchina"*

Installiamo il **webserver** 
>*apt-get install apache2*.<br>

Si creano **più siti** sulla stessa macchina aggiungendo file di configurazione in 
>*/etc/apache2/sites-avaiable/...*.<br>

Con il comando
>*cp 000-default.conf nomeFile.conf

creiamo una copia del file di default su cui poi potremmo lavorare
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
Aggiungere 3 nuovi **utenti**, uno per ogni server 
>*useradd -s /bin/bash -d /var/www/... -m nomeUtente*.<br>

Impostare la **password per ogni utente** 
>*passwd nomeUtente* --> *Inserimento della password*.<br>

Dopo la creazione degli utenti si vanno a dare i **permessi alle cartelle** 
>*chown -R nomeUtente:nomeUtente /var/www/cartellaSito*.<br>

## CHECKPOINT :white_check_mark:
Per controllare di avere creato in maniera adeguata gli utenti si controlla accedendo da **PuTTY** con i *nomiUtente* e le *Password* corrispondenti.

Facendo così si potrà sia scaricare che caricare file sulla cartella in **FTP** da remoto sul desktop attraverso Filezilla.<br>
